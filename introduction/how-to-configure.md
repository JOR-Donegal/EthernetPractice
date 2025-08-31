# How to configure

There are some customs and practices that experienced network engineers do that may not be obvious and are not in the manuals. I need to let you know about a few of these before we begin.

There are at least three ways to configure network equipment.

### The CLI

For my entire career, the _Command Line Interface_ (CLI) has been the main way to do configurations. It is hard to use, obscure, obsolete, pick an adjective with negative connotations! However, every competent engineer can use the CLI and in some ways this keeps things easy. Every experienced administrator has previous configurations they can keep in a text file. Extracting a configuration is a copy-and-paste and so is restoring a configuration. However, automation is difficult and inconsistent; we _screen-scrape_ systems by sending commands to them and parsing text from the responses. This is a truly terrible technique, but one we have honed over twenty years or more. I want to give some more detail here, because this sequence of practical work is based on the CLI.&#x20;

When I am working on a network device, it is normally through a terminal. I have an editor like NotePad++ running as well. I type my commands into the editor, make sure I am happy with them and then paste them to the device. My commands are thus documented and repeatable. There are complex scenarios where a device may have hundreds of lines of configuration. I do them nice and tidily in the editor, correcting as I am going along, adding comments. At the end of a sequence, my text file is my documentation and my backup; I can cut and paste the configuration into a replacement device if I need to. I recommend you adopt this approach very early on. Beware, there may be many stages of input to a CLI. Some devices/vendors allow you to enter commands, verify or parse them, and allow you to make corrections before you commit them. Familiarize yourself with the workings of a new CLI before you must use it in action.

### The GUI

The graphical user interface (GUI) does exist. It is good for visualization, management, and monitoring. It is less good for configuration. Documenting a GUI configuration may require many screenshots and the moment the vendor changes the GUI for something even more gaudy (which requires a non-supported version of Java and an insecure version of Flash), all the previous training, procedures and configurations need to be updated. There are reasons we use a GUI for configuration but on almost all modern equipment, if possible. Before I begin a configuration using the GUI, I will extract the configuration from the CLI and save it.  When I finish, I will again save the configuration which results from my actions at the GUI, and do a _diff_. I can now clearly see what change my work at the GUI really had.

### Application Program Interfaces (API)

The future is one where we will have well defined interfaces to interact with equipment, where we can send commands and configurations which are unambiguous, where instrumentation and telemetry have a powerful and easy to use command set. Progress is patchy and proprietary even with the most advanced equipment available. I am going to suggest you do some background reading on the underlined terms:

The term _Software Defined Networks_ (SDN) has morphed since it was introduced. To me it still means a separation of data from the management and control planes. It is now more commonly understood to mean programmability in networking. One of the academic aspirations is of building a network model and then configuring equipment based on that model. YANG models are a hot research topic, as is the NETCONF protocol, however, it can be hard to find equipment which supports it. When I work on Smart Grid and critical infrastructure, I may use equipment from [Schweitzer](https://selinc.com/products/communications/local-area-networks/ethernet-switches/). This will be SDN based.

The ultimate aspiration is network configuration based on what you want, without you having to know the details. Intent based networking is another major research topic.
