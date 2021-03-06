#
# $Revision: 1.4.2.5 $
#

WEKAHOME = .

.PHONY: all optimized debug clean install archive doc

all : 
	(cd core; make all)
	(cd classifiers; make all)
	(cd filters; make all)
	(cd estimators; make all)
	(cd associations; make all)
	(cd clusterers; make all)
	(cd attributeSelection; make all)

optimized : 
	(cd core; make optimized)
	(cd classifiers; make optimized)
	(cd filters; make optimized)
	(cd estimators; make optimized)
	(cd associations; make optimized)
	(cd clusterers; make optimized)
	(cd attributeSelection; make optimized)

debug :
	(cd core; make debug)
	(cd classifiers; make debug)
	(cd filters; make debug)
	(cd estimators; make debug)
	(cd associations; make debug)
	(cd clusterers; make debug)
	(cd attributeSelection; make debug)

clean : 
	(cd core; make clean)
	(cd classifiers; make clean) 
	(cd filters; make clean)
	(cd estimators; make clean)
	(cd associations; make clean)
	(cd clusterers; make clean)
	(cd attributeSelection; make clean)

doc :
	(cd ..; \
	javadoc -public -author -version -d doc \
	weka.core \
	weka.classifiers \
	weka.classifiers.j48 \
	weka.classifiers.m5 \
	weka.filters \
	weka.estimators \
	weka.associations \
	weka.clusterers \
	weka.attributeSelection; \
	for page in `ls doc/*.html`; \
	do cat $$page | sed "s/Index<\/a><\/pre>/Index<\/a>  <a href=\"http:\/\/www.cs.waikato.ac.nz\/ml\/weka\/index.html\">WEKA\'s home<\/a><\/pre>/g" > $$page.temp; mv $$page.temp $$page; done;\
	sed 's/API_users_guide.html/..\/Tutorial.pdf/g' \
	< doc/packages.html > packages_temp.html; \
	mv packages_temp.html doc/packages.html)

# Assumes any auxiliary classfiles are in the parent directory
# One of these must be SimpleCLI.class
install : all
	(cd ..; \
	echo "Main-Class: SimpleCLI" > manifest.tmp ;\
	jar cvfm $(WEKAHOME)/weka.jar manifest.tmp \
	*.class \
	weka/core/*.class \
	weka/classifiers/*.class \
	weka/classifiers/j48/*.class \
	weka/classifiers/m5/*.class \
	weka/filters/*.class \
	weka/estimators/*class \
	weka/associations/*.class \
	weka/clusterers/*.class \
	weka/attributeSelection/*.class ; \
	jar cvf $(WEKAHOME)/weka-src.jar \
        weka/core/*.java \
        weka/classifiers/*.java \
        weka/classifiers/j48/*.java \
        weka/classifiers/m5/*.java \
        weka/filters/*.java \
        weka/estimators/*java \
        weka/associations/*.java \
	weka/clusterers/*.java \
	weka/attributeSelection/*.java ;\
	rm manifest.tmp )
	javadoc -public -author -version -d $(WEKAHOME)/doc \
	weka.core \
	weka.classifiers \
	weka.classifiers.j48 \
	weka.classifiers.m5 \
	weka.filters \
	weka.estimators \
	weka.associations \
	weka.clusterers \
	weka.attributeSelection; \
	for page in `ls $(WEKAHOME)/doc/*.html`; \
	do cat $$page | sed "s/Index<\/a><\/pre>/Index<\/a>  <a href=\"http:\/\/www.cs.waikato.ac.nz\/ml\/weka\/index.html\">WEKA\'s home<\/a><\/pre>/g" > $$page.temp; mv $$page.temp $$page; done;\
	sed 's/API_users_guide.html/..\/Tutorial.pdf/g' \
	< $(WEKAHOME)/doc/packages.html > $(WEKAHOME)/packages_temp.html; \
	mv $(WEKAHOME)/packages_temp.html $(WEKAHOME)/doc/packages.html

archive :
	(cd ..; \
	tar czf archive/weka`date +%d%b%Y`.tar.gz  weka)





