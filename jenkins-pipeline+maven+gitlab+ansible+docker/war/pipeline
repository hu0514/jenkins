pipeline{
    agent any
    stages{
        stage('get code'){
            steps{
                git url: 'git@github.com:hu0514/DataPlatform.git', branch: 'master'
            }
        }
        stage('build'){
            agent {
                docker {
                    image 'maven:3-alpine'
                    args '-v /root/.m2:/root/.m2'
                }
            }
            steps{
                sh 'cd /var/jenkins_home/workspace/D&&mvn -B -DskipTests clean package'
            }
        }
        stage('test'){
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "test"
            }
            steps{
                echo "2"
            }
        }
        stage('fabu'){
            agent {
                docker {
                    image 'qq79428316/club-ansible:2.4.2.0'
                    args '-v /data/ansible:/etc/ansible -v /data/jenkins/data:/data -e ANSIBLE_HOST_KEY_CHECKING=False'
                }
            }
            steps{
                sh "ansible-playbook /etc/ansible/test.yml" 
            }
        }
            
    }
}