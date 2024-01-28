// pipeline {
//     agent any
//     stages{
//         stage("checkout"){
//             steps{
//                 checkout scm
//             }

//         }
//         stage("Test"){
//             steps{
//                 sh 'sudo apt-get install npm'
//                 sh 'npm test'
//             }
//         }
//         stage("Build"){
//             steps{
//                 sh 'npm run build'
//             }
//         }
//         stage("Build Image"){
//             steps{
//                 sh 'docker build -t my-node-app:1.0 .'
//             }
//         }
//         stage("Docker Push"){
//             steps{
//                 withCredentials([usernamePassword(credentialsId: 'docker_cred', passwordVariable: 'DOCKER_HUB_PASSWORD', usernameVariable: 'DOCKER_HUB_USERNAME')])
//                 {
//                     sh 'docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_PASSWORD'
//                     sh 'docker tag my-node-app:1.0 bayar/my-node-app:1.0'
//                     sh 'docker push bayar/my-node-app:1.0'
//                     sh 'docker logout'
//                 }
//             }
//         }
//     }
// }

pipeline {
    agent any
    stages{
        stage("checkout"){
            steps{
                checkout scm
            }

        }
        stage("Test"){
            steps{
                sh 'pip install npm'
                sh 'npm test'
            }
        }
        stage("Build"){
            steps{
                sh 'npm run build'
            }
        }
        stage("Build Image"){
            steps{
                sh 'docker build -t my-node-app:1.0 .'
            }
        }
        stage("Docker Push"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker_cred', passwordVariable: 'DOCKER_HUB_PASSWORD', usernameVariable: 'DOCKER_HUB_USERNAME')])
                {
                    sh 'docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_PASSWORD'
                    sh 'docker tag my-node-app:1.0 bayar/my-node-app:1.0'
                    sh 'docker push bayar/my-node-app:1.0'
                    sh 'docker logout'
                }
            }
        }
    }
}
