load('.tanzu/file_sync_only.py', 'file_sync_only')


#  './mvnw -Dmaven.test.skip=true -Dspring-boot.repackage.excludeDevtools=false package && rm -rf .build/* && unzip -o target/demo-*.jar -d .build/',
# local_resource(
#   'spring-demo-compile',
#   './mvnw -Dmaven.test.skip=true -Dspring-boot.repackage.excludeDevtools=false package && ' + 
#     'rm -rf target/jar-staging && ' +
#     'unzip -o target/demo-*.jar -d target/jar-staging && ' +
#     'rsync --delete --inplace --checksum -r target/jar-staging/ .build',
#   deps=['src', 'pom.xml'])

file_sync_only("hnandiwada/nginx",
    ["./deployment.yaml"],
    live_update=[
      sync('public/index.html', '/workspace/public/index.html'),
      run("#TODO: figure out how to restart the container; i.e. something like 'kill -HUP 1' that actually works")
    ],
)

k8s_resource(workload='nginx', port_forwards=8080)

