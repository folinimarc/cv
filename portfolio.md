# Portfolio Marc Folini

This is a selection of my professional and personal projects from the past few years, predominantly in the field of geographic information systems (GIS). *Disclaimer:* Due to non-disclosure agreements and intellectual property (IP) clauses, I am unable to provide source code and/or detailed insights into most of my past professional work.


*Table of Contents*
- [Certificate of Advanced Studies (CAS) Thesis: GIS Sandbox](#certificate-of-advanced-studies-cas-thesis-gis-sandbox)
- [GIS Frontend Technology Demo: The 1000 Largest Cities](#gis-frontend-technology-demo-the-1000-largest-cities)
- [Google Sheets Driven Content Management: Website of Science Slam Schweiz](#google-sheets-driven-content-management-website-of-science-slam-schweiz)
- [A Global Database of Physical Assets](#a-global-database-of-physical-assets)
- [Bringing Maps to MSCI's Client-Facing Platform](#bringing-maps-to-mscis-client-facing-platform)


## Certificate of Advanced Studies (CAS) Thesis: GIS Sandbox
*TL;DR:* Created a user-friendly GIS platform for educational use, leveraging Docker to eliminate setup issues and enhance learning experiences with preinstalled geospatial tools. A month-long thesis project within the scope of further education in GIS.

*Links:* [GitHub](https://github.com/folinimarc/os_gis_sandbox) | [Thesis PDF](https://github.com/folinimarc/os_gis_sandbox/blob/main/thesis/thesis.pdf)

*Keywords:* Thesis, Docker, Docker Compose, JupyterLab, GDAL, GeoServer, PostGIS, Educational Content.

#### Motivation
During my further education in GIS, a hands-on lecture on GDAL, a core library for geospatial data manipulation, was provided. The non-technical participants, using their own computers with various operating systems, spent over half of the lecture time resolving installation problems. This is not uncommon, as open-source GIS libraries often require non-trivial dependencies that can lead to compilation errors, version conflicts, and general frustration for non-technical users. More critically, by the time everything was operational, some participants were already frustrated and vowed never to use this library again. I had already been curious about container technology and its potential, and this scenario provided an opportunity to learn about it by addressing a real-world problem.

#### User Story
As a non-technical user interested in learning about GIS, I can start the GIS sandbox with minimal installation effort and a single command to gain access to fully functional open-source core technologies, including PostGIS, GeoServer, and a Python JupyterLab environment with GDAL and numerous Python GIS packages preinstalled. All components can interact with each other and with my computer's file system, allowing me to run experiments, process data, or embark on a learning path with the provided Data Story. This latter component is a data-driven, cross-component tutorial that teaches users how to create a bike suitability map in QGIS from raw open data from the city of Zurich. Once I no longer need the sandbox, I can easily shut it down or completely uninstall it within seconds without leaving any trace on my system.

#### Technical Details
This project utilizes container technology (Docker) and an orchestration layer (Docker Compose) to bypass the sometimes tedious installation processes of geospatial core libraries and applications. Some components of the sandbox are sourced from official distributors via DockerHub (GeoServer, PostGIS), while others (JupyterLab with GDAL and Python GIS packages, Data Story) are built and published to the GitHub container registry as part of this project, using GitHub Actions triggered by a semantic versioning system. This setup enables a user to download and start the sandbox from a single Docker Compose configuration file with one command. The use of Docker Compose networking and virtual volumes ensures components can retain configurations and installed packages across sandbox restarts and facilitate interactions among components.

#### Learnings
This project was essentially my first real engagement with container technologies. I navigated through many valleys of despair while forming my mental model of how images are created, stored, and utilized for container creation. The insights I gained have significantly advanced my professional work, where we have recently begun to adopt Docker and Kubernetes. The ease of working with PostGIS and GeoServer has inspired me to delve deeper into these technologies and apply them in my professional setting.

## GIS Frontend Technology Demo: The 1000 Largest Cities
*TL;DR:* A website built in a few hours using mature open-source libraries, where users can interact with a map and a table to explore the largest cities in the world.

*Links:* [Demo](https://folinimarc.github.io/poc-geo-frontend-cities/) | [GitHub](https://github.com/folinimarc/poc-geo-frontend-cities)

*Keywords:* Personal Project, Leaflet, DataTables, CSS Bootstrap, GitHub Actions, GitHub Pages.

#### Motivation
In my previous company, GIS was not yet widely used, and a lot of my work involved acting as a translator and educator between the engineering team, product team, and clients. Especially when it comes to the visual aspects of GIS, it's sometimes hard to convey what is readily available due to the hard work of others, and what is not. This motivated me to conduct a Sunday Hackathon to build a demo in a few hours, which loosely reflected one of our use cases—having tabular and map data interact with each other.

#### User Story
As a non-technical user, I can explore the map via pan and zoom, and select either a city marker by clicking it or select multiple cities using a lasso tool. In both cases, this will filter the table to display the selected cities. I can also sort and filter the table to explore city data and click a row to highlight the city on the map. By clicking the export button, I can download the current selection as a CSV file.

#### Technical Details
This project employs two established JavaScript libraries: Leaflet for interactive maps and DataTables for interactive tables and data export. It uses straightforward pure JavaScript to make them respond to user behavior. A rudimentary responsive layout is achieved using the CSS framework Bootstrap. The project is deployed as a static website hosted by GitHub Pages, which is redeployed upon each commit using GitHub Actions.

#### Learnings
Although I had used Leaflet and DataTables before, I learned new things about these libraries, such as the Leaflet Plugin system and the DataTables data export functionality. I enjoy working with JavaScript and learned about a controller pattern, whereby component-specific functionality is kept together and orchestrated by a controller. This project helped build a common understanding between stakeholders at work and allowed us to collaborate efficiently in shaping our product.

## Google Sheets Driven Content Management: Website of Science Slam Schweiz
*TL;DR:* A website that is super intuitive to update, because it uses a Google Sheet as the source for dynamic content.

*Links:* [Website](https://scienceslam.ch/de) | [GitHub](https://github.com/folinimarc/scienceslamschweiz/tree/main)

*Keywords:* Personal Project, Understand Your User, Python, Jinja2, Google Sheets, Science Slam, GitHub Actions, GitHub Pages.

#### Motivation
Science Slam is a competition where several slammers compete against each other in a scientific short presentation tournament, with all aids allowed. In the end, the audience decides on the champion of the evening. The network Science Slam Switzerland is a voluntary effort to make it easier for people to organize and/or perform Science Slams. We set out to build a website where crucial information could be updated by a diverse set of non-technical volunteers with minimal friction.

#### User Story
As a volunteer of the network, I can enter data about upcoming events simply in a Google Sheet, and I'm done. After midnight, the information appears on the website. I do not have to worry about cleaning up after the event, because outdated information is automatically removed.

#### Technical Details
Every day around midnight, a GitHub Action with a cron trigger runs a Python script to generate the static website files and pushes them to GitHub Pages for hosting. The Google Sheets API client is used to fetch the event data from the Google Sheet. This data is combined with other content, such as language-specific YAML files, using the Python Jinja2 template engine. The website uses the CSS framework Bootstrap for a responsive layout.

#### Learnings
The learnings from this project began even before the project started, when I tried to figure out why our website was already outdated despite using a sophisticated content management system. I learned that to encourage volunteers to use a technology, you sometimes have to think outside of a technical mindset and embrace unusual solutions. From a technological perspective, I enjoyed learning about the Google Sheets API and brushing up on my basic web technology skills.


## A Global Database of Physical Assets
*TL;DR:* Multi-year project to map out all physical assets of companies using a variety of technologies and processes.

*Links:* [This presentation at Google Next 2024 builds upon this project.](https://youtu.be/olGHj3j_hsY?si=5YkPNT95OMSWysdm)

*Keywords:* Professional Project, Technical Lead, Team Lead, Data Acquisition and Modelling, Python, Django, PostGIS, Azure Cloud, Azure DevOps, CI/CD, BigQuery, Google Cloud, Leaflet.

#### Motivation
Knowing the locations of offices, data centers, or plants of companies is key to modeling their susceptibility to climate risk. Such data is not readily available, which is why this multi-year project at MSCI was initiated.

#### User Story
As a climate risk researcher at MSCI, I have access to a high-quality dataset of millions of physical assets of companies with attributes such as coordinates, footprint, building type, and much more, allowing me to create elaborate models and perform statistical analysis.

#### Technical Details
Unfortunately, I can only provide a high-level overview here due to IP clauses. Data is collected from many different sources, including structured and unstructured, open-source and proprietary datasets. This happens through Databricks and a combination of Google Cloud services including BigQuery and VertexAI. Part of the data acquisition and quality control requires manual research, which is performed through a custom-built Python Django application with a PostGIS backend running in an Azure Kubernetes Cluster. Deployments are handled by CI/CD pipelines using Azure DevOps.

#### Learnings
As the technical lead, I learned more than I can possibly write down here over the years. Highlights include managing a small team of bright individuals, navigating the ever-exciting stormy waters, learning about the importance of software architecture and good practices when scaling up, building a complex system from scratch and maintaining it, and building large-scale geospatial data processing pipelines using Python.

## Bringing Maps to MSCI's Client-Facing Platform
*TL;DR:* This project introduces interactive maps with WMS layers about global physical hazard intensity to MSCI clients for the first time.

*Links:* [The maps are prominently featured in the product PDF.](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWOfc8)

*Keywords:* Professional Project, Technical Lead, QGIS, QGIS Server, Mapproxy, Python, GDAL, Kubernetes, Azure Cloud, CI/CD, Azure DevOps.

#### Motivation
There is a wealth of data that can be better interpreted and communicated when displayed on a map. During the revamp of the existing client-facing platform, I was tasked with building a common understanding of how we can present our global high-resolution physical hazard intensity datasets to clients in a meaningful way. I became the technical lead to conceptualize and deliver the end-to-end infrastructure, from cartography to incident response processes.

#### User Story
As a client of MSCI, I can visually explore, compare, and evaluate the impact of physical hazards on my portfolios in an intuitive and fast way.

#### Technical Details
Unfortunately, I can only provide a high-level overview here due to IP clauses. QGIS Server was used in a Kubernetes setup on Azure Cloud to provide a WMTS of styled physical hazard intensity maps. Mapproxy was used as a seeded cache in the same Kubernetes to reduce the latency of serving map tiles. These maps were created from multidimensional NetCDF files by automated pipelines leveraging Python Rasterio and GDAL. The frontend consisted of a React application with an embedded PowerBi dashboard with Mapbox GL JS.

#### Learnings
Processing global high-resolution raster datasets presents a few interesting resource-related challenges, which I learned to address. I also gained significant insights in terms of interacting with our brilliant research and client-facing teams to translate raw data into something meaningful for our clients, both on a data processing and cartographic level. Lastly, it was the first time for me conceptualizing and setting up a complete Kubernetes-based infrastructure with multiple environments, logging, and CI/CD pipelines.
