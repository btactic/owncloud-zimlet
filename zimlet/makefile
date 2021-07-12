all: zimlet

zimlet: clean
	zip -j -r cat_femprocomuns_owncloud_zimlet.zip *.*
	zip -u -r cat_femprocomuns_owncloud_zimlet.zip \
		help/*.* \
		ViewerJS/* \
		markdown/* \
		newDocTemplate/* \

clean:
	rm -f cat_femprocomuns_owncloud_zimlet.zip

.PHONY: all zimlet
