# Conference Fuzzy Shortcut to MSRC

...


Sentence Mining technique for learning machine

Human brain and sentence Mining
	Have to learn all 
	Break the sentence into parts:
		Memorizing sample sentences
		Recognize patterns and turning sample sentence into a sequence template
		Memorize vocabulary

	One fuzzing template revealed over 100 IE UAF vulnerabilies (blackHat Europe 2014)

	https://www.blackhat.com/docs/eu-14/materials/eu-14-Lu-The-Power-Of-Pair-One-Template-That-Reveals-100-plus-UAF-IE-Vulnerabilities.pdf

	Applying Sequence mining Technique over Power in Pairs to Generate Effective TestCase for Fuzzing

	Fuzzing Targets
		Windows based softwares HTML (Web Browsers and Outlook Render Engine)

	Template Mining
		Collect sample from sources
		Process collected webpages, identify scope where fuzzer can inject code
		Parse collected sample webpages and gather HTML/JS/CSS grammar
		Swap/inject fuzzer code into processed web pages
	
	Template Miner collect pages over the INternet
	Passes it in the pattern Determinator
	Use Grammar Identification, passes to Grammar Processor which use the Grammar Database
	Use scope Identification, which passes data to Fuzzer Friendly Database
	Combining the 2 endpoints, we can generate HTML and JS

	Template Gathering
		Collecting complex pages with rich JS /CSS
		Major Sources : JSFiddle, CSSDeck, LiveWeave

	Raw Template Processing & Pattern Recognition
		Regex voodoo magin on the template
		Tries to identify places in the templates where CSS / JS can be injected

	Pattern recognition
		Look for balises in pages
		Javascript code scope identification (uses { and } to determine scope)
		Javascript Statement Identification (identifies if, else, etc... to determine statement)
		CSS Selector Block Identification

	Vocabulary and Grammar Collection
		Mined Web Pages
		Existing Open Source Fuzzers
		W3Schools examples

	CSS Grammar Processing
		Grammar attribute and data type identification
		identifies Attribute name "top" and value "-300px"
		Create template top: <sign><value>px with it

	Javascript Grammar Collection & Challenges
		Difficult
		Full automation difficult - manual intervention required
		Uses JS DOM events 

	Demo : recreate a portrait with fuzzer
		Launch parser onto portrait with css
		Create a file containing all attributes and types of values associated
		

	End goal is to test if any faults in rendering html/CSS/JS is present
		Target MicrosoftEdgeCP.exe
		Unsigned DLL cannot be injected
		No fuzzing framework for edge
		Soon one to be open-sourced
		https://github.com/debasishm89/
	
	Demo Edge

	Application to Outlook Email Render Engine

		Supports HTML and CSS
		Same Testcase generator/grammar can be used to do fuzz test
		Using OpenXMolar (fuzzing framework OpenXML file format)
		
	Found many crashes on Edge and Outlook rendering engine
	Vulnerabilies reported, made it to MSRC Top 100
	Pattern recognition and test case generation will be open-sourced
	
