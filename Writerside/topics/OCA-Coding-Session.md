# Coding Session 0

> Session del 25/06/2024 - 18:05
> {style="note"}

> Commit:
> <a href="https://github.com/borghes3/oca/commit/524db4732288449db3306e6449cd8801871b9608">@borghes3/oca/524db47</a>

## Objective List
- Creare il progetto NextJS
- Comprendere l'implementazione di IPFS tramite Helia 

## Sviluppo

### Progetto NextJS
Creato il progetto di base di NextJS tramite 
<code>npx create-next-app</code>.<br/>

### Lettura docs
Ho iniziato con una lettura rapida delle 
<a href="https://docs.ipfs.tech/concepts/what-is-ipfs/#defining-ipfs">Basics di IPFS </a>,
il loro sito propone alcune idee interessanti per l'applicazione di IPFS, che si propone più come
un **protocollo** che come un servizio di cloud data hosting.<br/>
Successivamente si passa alla documentazione (molto scarsa) di Helia, praticamente _useless_.<br/>
Ho trovato in compenso una serie di esempi di utilizzo di Helia tra cui
<a href="https://github.com/ipfs-examples/helia-examples/tree/main/examples/helia-nextjs">Helia with NextJS</a>.<br/>

#### Riferimento a Pump.fun
Ho scoperto che potrei usare in maniera molto più semplice un servizio di IPFS chiamato
<a href="https://pinata.cloud">Pinata</a>,
**lo stesso utilizzato da pump.fun**, ma costituirebbe un costo per l'applicazione,
concetto che va contro quello di questo progetto, **dobbiamo decentralizzare**.<br/>

### Esempio Helia-NextJS
Analizzando il progetto di esempio trovato sulla repo di Helia non emerge molto se non un component React molto 
semplice ma molto utile, il file in questione è
<code>
    <a href="https://github.com/ipfs-examples/helia-examples/blob/main/examples/helia-nextjs/components/ipfs.js">ipfs.js</a>
</code>.
Di seguito un copia incolla per non averlo su github in caso di modifiche, ad oggi risulta:

```Typescript
import { createHelia } from 'helia'
import { React, useState, useEffect } from 'react'

const IpfsComponent = () => {
    const [id, setId] = useState(null)
    const [helia, setHelia] = useState(null)
    const [isOnline, setIsOnline] = useState(false)

    useEffect(() => {
        const init = async () => {
            if (helia) return
            const heliaNode = await createHelia()
            const nodeId = heliaNode.libp2p.peerId.toString()
            const nodeIsOnline = heliaNode.libp2p.status === 'started'
            setHelia(heliaNode)
            setId(nodeId)
            setIsOnline(nodeIsOnline)
        }
        init()
    }, [helia])

    if (!helia || !id) {
        return (<h4>Starting Helia...</h4>)
    }

    return (
        <div>
            <h4 data-test="id">ID: {id.toString()}</h4>
            <h4 data-test="status">Status: {isOnline ? 'Online' : 'Offline'}</h4>
        </div>
    )
}
export default IpfsComponent
```
i cui punti chiave risultano:

- <code><a href="https://helia.io/functions/helia.createHelia.html">createHelia()</a></code> crea e ritorna un nuovo _nodo_ Helia
- Il valore ritornato dal punto precedente è un
<code><a href="https://helia.io/interfaces/helia.HeliaLibp2p.html#:~:text=HeliaheliaHeliaLibp2p-,Interface%20HeliaLibp2p%3CT%3E,-The%20API%20presented">Interface HeliaLibp2p</a></code>
- <code>nodeId</code> prende l'ID del nodo dalla proprietà <code>libp2p.peerId</code> del punto precedente convertendolo in stringa
- <code>nodeIsOnline</code> prende lo stato del nodo verificando che <code>libp2p.status === 'started'</code> (occhio al tipo, triplo uguale)
- Il resto è semplicissimo react con <code>useState()</code> e <code>useEffect()</code>, nulla di nuovo

### Riflessioni su Helia e IPFS in generale
Si può concludere in via generale che Helia, non si pone come un "provider" o "gateway" per interagire con IPFS,
ma come da documentazione IPFS _(IPFS è da intendersi come un protocollo)_ è semplicemente un set di strumenti che 
**rispetta le regole di IPFS** e di conseguenza una valida alternativa per interagirci tramite un API con 
Javascript/Typescript.

## Note
Nessuna