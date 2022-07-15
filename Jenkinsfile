pipeline {
    agent any
    environment {
        REPO = " HenriO354/caesar-cipher-1 "
    	}
    stages {
        stage('Preparing gradlew') {
            steps {
                sh 'chmod +x gradlew'
            }
        }
        stage('test') {
            steps {
                sh './gradlew test'
            }
        }
        stage('build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('Release') {
            steps {
                sh 'token="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"'
                sh 'tag=$(git describe --tags)'
                sh 'message="$(git for-each-ref refs/tags/$tag --format=\'%(contents)\')"'
                sh 'name=$(echo "$message" | head -n1)'
                sh 'description=$(echo "$message" | tail -n +3)'
                sh 'release=$(curl -XPOST -H "Authorization:token $token" --data \'{"tag_name": "$tag", "target_commitish": "main", "name": "$name", "body": "$description", "draft": false, "prerelease": false}\' "https://api.github.com/repos/HenriO354/caesar-cipher-1/releases/")' 
                
            }
        }
        stage('Artefact Upload') {
            steps {

                sh 'tag=$(git describe --tags)'
                sh 'upload=$(curl -XPOST -H "Authorization:token $token" -H "Content-Type:application/octet-stream" --data-binary @build/libs/caesar-cipher.jar "https://uploads.github.com/repos/HenriO354/caesar-cipher-1/releases/$tag/assets?name=caesar-cipher.jar")' 
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}