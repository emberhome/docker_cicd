include ../../../make.inc

check_variables:
	@echo HOSTNAME=${HOSTNAME}
	@echo DOCKER_IMAGE_NAME=${DOCKER_IMAGE_NAME}
	@echo PORT=${PORT}
	@echo europe-west1-docker.pkg.dev/${PROJECT_ID}/${REPOSITORY}/${IMAGE_NAME}:${IMAGE_TAG}


build_docker_image:
	docker build -t ${DOCKER_IMAGE_NAME}:${IMAGE_TAG} -f dockerfile-task-3-1 .

run_docker_image:
#docker run --rm -it -p 8000:8000 ${DOCKER_IMAGE_NAME}:${IMAGE_TAG}
	docker run -it --rm -p ${PORT}:${PORT} -e PORT=${PORT} ${DOCKER_IMAGE_NAME}:${IMAGE_TAG}

tag_docker_image:
	docker tag "${IMAGE_NAME}:${IMAGE_TAG}" "${HOSTNAME}/${PROJECT_ID}/${REPOSITORY}/${IMAGE_NAME}:${IMAGE_TAG}"

push_docker_image:
	docker push "${HOSTNAME}/${PROJECT_ID}/${REPOSITORY}/${IMAGE_NAME}:${IMAGE_TAG}"

deploy_docker_image:
	gcloud run deploy fast-app \
	--image europe-west1-docker.pkg.dev/${PROJECT_ID}/${REPOSITORY}/${IMAGE_NAME}:${IMAGE_TAG} \
	--region=europe-west1 \
	--allow-unauthenticated

#image europe-west1-docker.pkg.dev/${PROJECT_ID}/${REPOSITORY}/${IMAGE_NAME}:${IMAGE_TAG}
#image europe-west1-docker.pkg.dev/airy-aria-450311-u1/api/base-image-emma:prod
