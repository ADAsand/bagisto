pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // ������룬��һ�����Ը�����Ҫ����SCM�Ͳֿ�URL
                // ���磬����ʹ��Git SCM���
                checkout([$class: 'GitSCM', branches: [[name: 'master']], 
                          userRemoteConfigs: [[url: 'https://github.com/Ryann727/bagisto.git']]])
            }
        }
        stage('Build') {
            steps {
                // ������׶�ִ�� composer install ����
                sh 'composer install'
            }
        }
        stage('Release') {
            steps {
                // ������׶�ִ�� php artisan serve ���ǰ̨���У�
                sh 'php artisan serve'
            }
        }
        stage('Unit Test') {
            steps {
                // ������׶�ִ�е�Ԫ����
                sh 'php vendor/bin/codecept run unit'
            }
        }
        // ������Ӹ���׶Σ��粿���
    }
    post {
        success {
            // �����ɹ�ʱ�Ĳ���
            // �ڴ˴����Դ�������������֪ͨ
        }
        failure {
            // ����ʧ��ʱ�Ĳ���
            // �ڴ˴����Դ�������������֪ͨ
        }
    }
}
