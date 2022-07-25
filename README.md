# AgentHospital Project


### Istruzioni per l'avvio

<ol>
  <li>Mandare un messaggio all'infermiera dicendole di aprire le porte. (Di seguito il codice).</li>
  <li>Insert name of addressee: infermiera.</li>
  <li>Insert From: user.</li>
  <li>Insert message: send_message(apri_visite,user).</li>
</ol>

### Descrizione del mas.
<p text-align="justify">In questo mas abbiamo 3 tipi di agenti: il medico, il paziente e l'infermiera. L'obiettivo dell'infermiera è quello di aprire le porte del pronto soccorso. Quindi attraverso l'evento apri_visiteE 'sveglia' gli agenti pazienti e li fa entrare in ospedale.
l'agente paziente è instanziato nell'esempio 3 volte, esso mantiene attraverso un fact l'ID e la Priorità che ha della per la visita. Esso viene svegliato come detto precedentemente dall'infermiera attraverso l'evento arriva_ospedaleE, a questo evento ne consegue l'azione avvisa_medicoA che semplicemente manda l'avviso al medico che il paziente necessita di una visita, mandandogli l'ID e la Priorità, ma non ancora avviene la visita! Sarà il medico a decidere quando dovrà essere visitato il paziente. L'agente medico invece mantiene un proprio stato interno (stato_medico) che è true/false, true se il medico non è occupato, false se è occupato. Quando arrivano i pazienti (cosa che avviene nel momento che l'infermiera apre le porte) il medico valuta in base al tempo di arrivo e alla priorità quale paziente visitare prima. Priorita 1 significa che ha bisogno di essere visitato immediatamente, 2 è una situazione intermedia, 3 invece riguarda i paziente con probblemi che possono essere gestiti per ultimo ovvero meno gravi rispetto agli altri 2. Quando arriva il paziente quindi il medico utilizza il fact ticket_paziente che è una tripla composta da (ID,Priorità,Tempo_di_Arrivo) e la salva in una lista. A questo punto, proattivamente il medico decide in base ai ticket che ha, quale paziente visitare. Ciò viene fatto attraverso lo stato interno del medico, più precisamente con stato_medicoI, ovvero se è libero prova a gestire i pazienti, la gestione dei pazienti è un'azione che utilizza la lista dei ticket dei pazienti, e valuta in base a priorità e arrivo (a pari priorità vale il tempo di arrivo inferiore) decide quale paziente visitare, una volta deciso quale paziente visitare il suo stato_medico diventa false, ovvero è "occupato" e procede con l'accettazione del paziente attraverso l'azione accettazione_pazienteA. L'accettazione del paziente consiste nel contattare il paziente invitandolo ad entrare nello studio del medico per la visita.  Il paziente a questo punto si fa visitare e a visita terminata l'agente paziente manda un messaggio all'agente medico che terminerà definitivamente la visita, eliminando il ticket del paziente appena visitato e procederà con la liberazione della stanza. L'azione di liberazione della stanza consiste nel settare lo stato del medico a true rendendolo "disponibile" ad ulteriori visite se ci sono.</p>
