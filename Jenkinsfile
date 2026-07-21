// Job A - build del core iDempiere (l'intero reactor Tycho in questo repo).
//
// Serve perche' TUTTI i job di plugin (ms-plugins e idempiere-base, Livello 1)
// referenziano org.idempiere.p2/target/repository come target platform del
// core (via file:///${repos.idempiere}/org.idempiere.p2/target/repository,
// impostato da -Drepos.idempiere=/opt/repos/idempiere). Senza questo job
// eseguito almeno una volta, quella cartella non esiste e ogni build di
// plugin fallisce con "No repository found at file:////opt/repos/idempiere/...".
//
// Trigger: pollSCM, il core cambia raramente rispetto ai singoli plugin.
//
// Nessun upload/publish qui: l'output resta nel checkout locale
// (org.idempiere.p2/target/repository) e viene letto direttamente dagli altri
// job via path assoluto sullo stesso agent, non pubblicato altrove.

pipeline {
    agent {
        label 'master'
    }

    options {
        timestamps()
    }

    stages {
        stage('Build core') {
            steps {
                sh 'mvn clean verify'
            }
        }
    }
}
