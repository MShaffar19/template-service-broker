FROM registry.svc.ci.openshift.org/openshift/builder:golang-1.12 AS builder
WORKDIR /go/src/github.com/openshift/template-service-broker
COPY . .
RUN make build --warn-undefined-variables

FROM centos:7
COPY --from=builder /go/src/github.com/openshift/template-service-broker/template-service-broker /usr/bin/
ENTRYPOINT ["/usr/bin/template-service-broker"]
LABEL io.k8s.display-name="OpenShift Template Service Broker" \
      io.k8s.description="This is a component of OpenShift, it gives the service catalog visibility of the default Instant App and Quickstart templates" \
      com.redhat.component="template-service-broker" \
      name="openshift/ose-template-service-broker" \
      io.openshift.tags="openshift, template-service-broker"
