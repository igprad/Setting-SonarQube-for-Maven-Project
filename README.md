1. Install Maven
2. Install Sonarqube dan sonar scanner
3. Jika belum ada, buat path $JAVA_HOME ke arah jdk anda
4. Jika belum ada, buat path untuk maven
5. Opsional : Buat settings.xml maven anda agar terintegrasi dengan sonarqube:

		<settings>
		    <pluginGroups>
			<pluginGroup>org.sonarsource.scanner.maven</pluginGroup>
		    </pluginGroups>
		    <profiles>
			<profile>
			    <id>sonar</id>
			    <activation>
				<activeByDefault>true</activeByDefault>
			    </activation>
			    <properties>
				<!-- Optional URL to server. Default value is http://localhost:9000 -->
				<sonar.host.url>
				  http://myserver:9000
				</sonar.host.url>
			    </properties>
			</profile>
		     </profiles>
		</settings>
	

6. Buat manual sonar-project.properties isinya:

		# must be unique in a given SonarQube instance
		sonar.projectKey=my:project
		
		# this is the name and version displayed in the SonarQube UI. Was mandatory prior to SonarQube 6.1.
		sonar.projectName=My project
		sonar.projectVersion=1.0
		 
		# Path is relative to the sonar-project.properties file. Replace "\" by "/" on Windows.
		# Since SonarQube 4.2, this property is optional if sonar.modules is set. 
		# If not set, SonarQube starts looking for source code from the directory containing 
		# the sonar-project.properties file.
		sonar.sources=.
		 
		# Encoding of the source code. Default is default system encoding
		#sonar.sourceEncoding=UTF-8
		
Opsi 1 :

7. Jalankan sonar yang sudah didownload di : https://www.sonarqube.org/downloads/
8. Lalu lakukan melalui terminal perintah : mvn clean verify sonar:sonar
9. Buka UI Sonar sesuai host yang anda daftarkan


Opsi 2 (Jika gagal Opsi 1):

7. Jika sudah, maka langkah berikutnya adalah masuk ke direktori projek yang hendak di analisa melalui cmd pada windows
	kemudian lakukan perintah (1 baris 1 kali dilakukan)
	
		mvn clean verify sonar:sonar
		mvn clean install
		mvn sonar:sonar
		mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.1.1:sonar
		
8. Seharusnya projek anda sudah dapat di analisa, saatnya menjalankan sonar-sanner melalui pemanggilan
	direktori-anda:\lokasiscannersonar\bin\sonar-scanner.bat

9. Buka localhost:9000, maka anda dapat melihat hasil scan.
