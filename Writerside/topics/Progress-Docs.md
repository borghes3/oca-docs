# OCA Progress Docs

## Introduzione

Questa documentazione _(Progress Docs in futuro)_ riporta tutte le fasi dello sviluppo di **OCA _(On-Chain Archive)_**
progetto personale che si pone come un sistema di archiviazione basato sulla
<a href="https://solana.com/">Blockchain di Solana</a> 
e su 
<a href="https://ipfs.tech/">IPFS</a>.<br/>
La documentazione si sviluppa da un principio di competenze _entry level_ in ambito blockchain per svilupparsi man mano 
con il progetto.
Il progetto nasce per puro scopo ludico e al fine di sviluppare le competenze del programmatore in ambito blockchain 
partendo da una base di conoscenza avanzata in ambito di _Web Development Fullstack_.

### Repository del Progetto

Il progetto in sè può essere consultato tramite Version Control al link
<a href="https://github.com/borghes3/oca">@borghes3/oca</a>
su Github, la repository è al momento della stesura privata per discrezione personale.

## Idea

Il progetto si pone come obbiettivo quello di lavorare sulla blockchain con un approccio _hands-on_ al fine di
apprendere nella maniera più efficace gli aspetti fondamentali dello storage
<a href="https://ipfs.tech/">IPFS</a> 
e dei 
<a href="https://solana.com/docs/core/programs">Programs</a> 
_(Smart Contracts su altre blockchain)_.

## Struttura dei Progress Docs

La documentazione sarà suddivisa in diversi moduli denominati **Coding Sessions** che rappresentano sessioni di sviluppo
contenenti tutte le idee e implementazioni attuate in una sessione di sviluppo.
<br/>
Una volta completata la coding session, i Progress Docs verranno aggiornati allegando alla pagina del progresso,
il link al commit sulla repository principale _(mantenuta privata per discrezione personale)_.

## Tech Stack (in aggiornamento)

<table>
	<thead>
		<tr>
			<td>Strumento</td>
			<td>Applicazione</td>
			<td>Note</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><a href="https://nextjs.org/">NextJS</a></td>
			<td>Sviluppo dell'applicazione web</td>
			<td>Gestione dell'UI e dell'aspetto web <i>off-chain</i></td>
		</tr>
        <tr>
			<td><a href="https://ipfs.tech/">IPFS</a></td>
			<td>Gestione decentralizzata dei dati</td>
            <td>Non si utilizza un salvataggio diretto on-chain visti i costi di gestione e <a 
                href="https://solana.com/docs/core/accounts#:~:text=Accounts%20can%20store%20up%20to%2010MB%20of%20data">
            limitazioni a 10MB</a></td>
		</tr>
        <tr>
			<td><a href="https://solana.com/">Solana</a></td>
			<td>Salvataggio degli hash IPFS</td>
			<td>Possibile implementazione di Smart Contracts (Programs) in base alle necessità</td>
		</tr>
        <tr>
			<td><a href="https://fleek.xyz/">Fleek</a></td>
			<td>Deployment del progetto stesso su IPFS e hosting</td>
			<td>In valutazione, sarà considerato nel momento del deployment in production</td>
		</tr>
	</tbody>
</table>