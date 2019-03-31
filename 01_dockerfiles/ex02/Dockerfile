FROM ruby

RUN apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install nodejs -y && \
	gem install rails

EXPOSE 3000

ONBUILD COPY .	/opt/app

ONBUILD WORKDIR	/opt/app

ONBUILD	RUN bundle install && \
			rake db:migrate && \
			rake db:seed
