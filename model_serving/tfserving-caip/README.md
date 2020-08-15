# Serving TensorFlow 2.x models using AI Platform Prediction Custom Containers and TF Serving

This repo contains code samples that demonstrate how to serve TensorFlow 2.x models using AI Platform Prediction Custom Containers (Beta) and [TensorFlow Serving](https://www.tensorflow.org/tfx/guide/serving). 

The code samples utilize the [ResNet101 image classification model](https://tfhub.dev/google/imagenet/resnet_v2_101/classification/4) from TensorFlow Hub. The design patterns and techniques demonstrated in the samples can be easily adapted to other domains and types of models.

## The repo content:
[01-prepare-for-serving.ipynb](01-prepare-for-serving.ipynb). This notebook shows how to prepare a TensorFlow 2.x model for serving. The notebook covers:
 * Re-using pre-trained models from TensorFlow Hub
 * Enhancing a pre-trained model with pre-processing and post-processing graphs
 * Defining multiple serving signatures
 
[02-deploy-to-aipp.ipynb](02-deploy-to-aipp.ipynb). This notebook walks you through the process of deploying a [TensorFlow SavedModel](https://www.tensorflow.org/guide/saved_model) to AI Platform Prediction using a [TensorFlow Serving container image](https://hub.docker.com/r/tensorflow/serving). The notebook covers:
* Using AI Platform Prediction (Beta) Management REST API
* Configuring TensorFlow Serving model server
* Testing a deployed model version

[03-perf-testing.ipynb](03-perf-testing.ipynb). This notebook demonstrates how to use an open source load testing tool [Locust](locust.io), [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine) and [Cloud Monitoring](https://cloud.google.com/monitoring) to perform load testing of a model version deployed in AI Platform Prediction. The notebook covers:
* Deploying Locust to a [GKE cluster](https://cloud.google.com/kubernetes-engine)
* Creating custom [Cloud Monitoring](https://cloud.google.com/monitoring) dashboards
* Preparing and running load tests
* Retrieving and consolidating test results

[04-analyze-tests.ipynb](04-analyze-tests.ipynb). This notebook outlines techniques for analyzing load test results. The notebook covers:
* Aligning and normalizing metric time series
* Using Pandas and Matplotlib to analyze and visualize test results

[locust](locust). This folder contains [Kustomize](https://kustomize.io/) manifests to deploy Locust to a GKE cluster and a [locustfile](https://docs.locust.io/en/stable/writing-a-locustfile.html) script demonstrating how to load test the AI Platform Prediction REST API `predict` method.

[test_results](test_results). This folder contains examples of test metrics captured while running tests following the process described in `03-perf-testing.ipynb`. The samples are used by the `04-analyze-test.ipynb` notebook

[test_images](test_images). This folder contains sample images used during testing of the ResNet101 model

[dashboard_template](dashboard_template). This folder contains an example of a custom [Cloud Monitoring dashboard](https://cloud.google.com/monitoring/dashboards) that demonstrates how to aggregate the standard [AI Platform Prediction metrics](https://cloud.google.com/monitoring/api/metrics_gcp#gcp-ml) with custom [Cloud Logging log-based metrics](https://cloud.google.com/logging/docs/logs-based-metrics) based on Locust test statistcs.

## Environment setup

The code samples where tested on [AI Platform Notebooks](https://cloud.google.com/ai-platform-notebooks) using the standard TensorFlow 2.2 image. 




