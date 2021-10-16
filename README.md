# axum_sample

## setup
```sh
$ docker-compose build
$ docker-compose up
```

## usage
```sh
# hello_world
$ curl http://localhost:8080
> Hello, World!
```

## deploy for Cloud Run
```sh
# gcloud auth docker
# cf. https://cloud.google.com/artifact-registry/docs/docker/quickstart?hl=ja#auth
$ gcloud auth configure-docker asia-northeast3-docker.pkg.dev

# add tag
# cf. https://cloud.google.com/artifact-registry/docs/docker/quickstart?hl=ja#tag
$ docker tag axum_sample_axum_sample asia-northeast3-docker.pkg.dev/otegal-dev/axum-sample/axum-sample

# check image
$ docker images

# push Artifact Registory
# need created artifact registory repository
# cf. https://cloud.google.com/artifact-registry/docs/docker/quickstart?hl=ja#push
$ docker push asia-northeast3-docker.pkg.dev/otegal-dev/axum-sample

# deploy Cloud Run
# cf. https://cloud.google.com/artifact-registry/docs/integrate-cloud-run#deploy
# ex. gcloud run deploy --image asia-northeast3-docker.pkg.dev/otegal-dev/axum-sample/axum-sample
$ gcloud run deploy --image REPO-LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY/IMAGE

```

`gcloud run deploy`コマンドが完了したら`Service URL`に記載してあるURLにアクセスすれば動作確認を行えます。

## memo
Cloud Runではデフォルトで開いているポートは`8080`らしいです。

