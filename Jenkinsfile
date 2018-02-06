#!/usr/bin/env groovy

node('master') {
    try {
        stage('build') {
            checkout scm
            sh "echo 'ENV SETUP'"
            sh "composer install"
            sh "cp .env.example .env"
            sh "php artisan key:generate"
        }

        stage('test') {
             sh "echo 'Running Test'"
             sh "php artisan serve &"
             sh "php artisan dusk"

        }

        stage('deploy') {
            // ansible-playbook -i ./ansible/hosts ./ansible/deploy.yml
            sh "echo 'WE ARE DEPLOYING'"
        }
    } catch(error) {
        throw error
    } finally {

    }

}
