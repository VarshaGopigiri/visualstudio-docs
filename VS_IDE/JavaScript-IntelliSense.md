---
title: "JavaScript IntelliSense"
ms.custom: na
ms.date: 10/03/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - vs-ide-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# JavaScript IntelliSense
IntelliSense helps you write code faster and with fewer errors by providing information while you code. As you work with client script in the JavaScript editor, IntelliSense lists the objects, functions, properties, and parameters that are available based on your current context. You can select a coding option from the pop-up list provided by IntelliSense to complete the code.  
  
 IntelliSense makes it easier to complete the following tasks:  
  
-   Find member information.  
  
-   Insert language elements directly into your code.  
  
-   Maintain your context without having to leave the code editor.  
  
-   Support custom IntelliSense with XML documentation comments and JavaScript IntelliSense extensibility.  
  
 This topic contains the following sections:  
  
-   [Determining IntelliSense Context](#DeterminingIntelliSenseContext)  
  
-   [Processing IntelliSense Information](#ProcessingIntelliSenseInformation)  
  
-   [JavaScript IntelliSense Features](#Features)  
  
-   [JavaScript IntelliSense Extensibility](#Extensibility)  
  
-   [JavaScript Validation](#Validation)  
  
 For more information about the IntelliSense functionality of Visual Studio, see [Using IntelliSense](../VS_IDE/Using-IntelliSense.md).  
  
##  <a name="DeterminingIntelliSenseContext"></a> Determining IntelliSense Context  
 JavaScript IntelliSense provides coding choices based on all script that is relevant to your current script context. This includes scripting elements in the current file. It also includes any code that is referenced directly or indirectly from your script, such as script file references, assembly script references, service references, and page-associated references.  
  
 Your current script context is created based on the following items:  
  
-   Functions that are defined in all script blocks in the active document. Inline script blocks are supported in files that have the file-name extensions .aspx., .ascx, .master, .html, and .htm.  
  
-   `script` elements with `src` attributes that point to another script file. The target script file must have the file-name extension .js.  
  
-   JavaScript files that reference other JavaScript files by using a `reference` directive.  
  
-   Reference groups for global objects, IntelliSense extensions, or delay-loaded script files.  
  
-   References to XML Web services.  
  
-   The <xref:System.Web.UI.ScriptManager?qualifyHint=False> and <xref:System.Web.UI.ScriptManagerProxy?qualifyHint=False> controls, if the Web application is an AJAX-enabled ASP.NET application.  
  
-   The Microsoft Ajax Library, if you are working in an AJAX-enabled ASP.NET Web application.  
  
    > [!NOTE]
    >  IntelliSense is not supported for script that is in event-handler attributes on HTML elements, or that is defined in `href` attributes.  
  
##  <a name="ProcessingIntelliSenseInformation"></a> Processing IntelliSense Information  
 To provide JavaScript IntelliSense, the language service performs the following operations:  
  
-   Creates a list of dependent JavaScript files that are based on references in the active document, and based on recursively examining script references in the referenced files.  
  
-   Traverses the list and collects type information and other relevant data from each file.  
  
-   Aggregates the data and passes it to the JavaScript language service, which makes the type information and data available to IntelliSense.  
  
-   Monitors the files for changes that might affect the IntelliSense list and updates the list as needed. Scripts on remote stores (such as those referenced using HTTP) do not get monitored.  
  
##  <a name="Features"></a> JavaScript IntelliSense Features  
 JavaScript IntelliSense supports the following objects:  
  
-   [Document Object Model (DOM) elements](#HTMLDom)  
  
-   [Intrinsic objects](#IntrinsicObjects)  
  
-   [User-defined variables, functions, and objects](#UserDefined)  
  
-   Objects defined in external files using references such as [script references](#Script), [reference directives](#ReferenceDirectives), and [reference groups](#ReferenceGroups).  
  
-   Objects defined in remote files that are downloaded by Visual Studio.  
  
-   Objects specified in [XML documentation comments](#XMLDocComments), such as parameters and fields.  
  
-   Objects described using standard JavaScript comment tags (//). For more information, see [Extending JavaScript IntelliSense](../VS_IDE/Extending-JavaScript-IntelliSense.md).  
  
-   Objects supported using the [JavaScript IntelliSense Extensibility](#Extensibility) mechanism. For more information, see [Extending JavaScript IntelliSense](../VS_IDE/Extending-JavaScript-IntelliSense.md).  
  
-   [ASP.NET AJAX objects](#ASPNet)  
  
 When IntelliSense is unable to determine the type of an object, it provides options for statement completion using identifiers in the active document. For more information, see [Statement Completion for Identifiers](../VS_IDE/Statement-Completion-for-Identifiers.md).  
  
###  <a name="HTMLDom"></a> HTML DOM Elements  
 JavaScript IntelliSense provides programming references for Dynamic HTML (DHTML) DOM elements, such as `body`, `form`, and `div`. Only the elements that are included in the current document and master page are displayed by IntelliSense. JavaScript IntelliSense also supports the `window` and `document` objects and their members.  
  
###  <a name="IntrinsicObjects"></a> Intrinsic Objects  
 JavaScript IntelliSense provides programming references for intrinsic objects such as `Array`, `String`, `Math`, `Date`, and `Number`. For more information about intrinsic objects, see [Intrinsic Objects](../Topic/Intrinsic%20Objects%20\(JavaScript\).md).  
  
###  <a name="UserDefined"></a> User-defined Variables, Functions, and Objects  
 When you change a JavaScript file, Visual Studio scans opened and referenced documents to determine all available code resources. This includes the variables, functions, and objects that you have created. These resources are then available to JavaScript IntelliSense.  
  
 For more information about user-defined variables, functions, and objects, see [Creating Your Own Objects](http://go.microsoft.com/fwlink/?LinkId=108671) on the MSDN website.  
  
###  <a name="External"></a> External File References  
 You can include various types of external file references to achieve IntelliSense support in your code. External file references may be script references, reference directives, or they can be specified using reference groups.  
  
####  <a name="Script"></a> Script References  
 Instead of writing all client script in a page, you can reference external files that include scripting code. This makes it easier for you to reuse code between pages, and it enables client script to be cached by the browser.  
  
 If you are not working with an ASP.NET AJAX-enabled Web page, you can reference an external script file by using the `src` attribute in the opening tag of a `script` element. The `src` attribute specifies the URL to an external file that contains the source code or data.  
  
 The following example shows markup that uses the `src` attribute in a <`script`> tag to reference a script file.  
  
```html  
<script type="text/javascript" src="~/Scripts/JavaScript.js">  
  
</script>  
```  
  
 If you are working with an ASP.NET AJAX-enabled Web page, you can reference script files by using the <xref:System.Web.UI.ScriptReference?qualifyHint=False> object of the <xref:System.Web.UI.ScriptManager?qualifyHint=False> control.  
  
 The following example shows markup that uses a <xref:System.Web.UI.ScriptReference?qualifyHint=False> object in a <xref:System.Web.UI.ScriptManager?qualifyHint=False> control to reference a script file.  
  
```html  
<asp:ScriptManager ID="ScriptManager1" runat="server">  
  <Scripts>  
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />  
  </Scripts>  
</asp:ScriptManager>  
```  
  
 IntelliSense also supports script files that are embedded as resources in an assembly in ASP.NET AJAX Web applications. For more information about embedded script resources, see [Walkthrough: Embedding a JavaScript File as a Resource in an Assembly](../Topic/Walkthrough:%20Embedding%20a%20JavaScript%20File%20as%20a%20Resource%20in%20an%20Assembly.md).  
  
####  <a name="ReferenceDirectives"></a> Reference Directives  
 A `reference` directive enables Visual Studio to establish a relationship between the script you are currently editing and other scripts. The `reference` directive lets you include a script file in the scripting context of the current script file. This enables IntelliSense to reference externally defined functions, types, and fields as you code.  
  
 You create a `reference` directive in the form of an XML comment. The directive must be declared earlier in the file than any script. A `reference` directive can include a disk-based script reference, an assembly-based script reference, a service-based script reference, or a page-based script reference.  
  
 The following example shows examples of using disk-based reference directives. In the first example, the language service looks for the file in the same folder that contains the project file (for example, .jsproj).  
  
 `/// <reference path="ScriptFile1.js" />`  
  
 `/// <reference path="Scripts/ScriptFile2.js" />`  
  
 `/// <reference path="../ScriptFile3.js" />`  
  
 `/// <reference path="~/Scripts/ScriptFile4.js" />`  
  
 The following example shows how to create a reference to an assembly-based script.  
  
 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`  
  
 The following example shows how to reference service-based script:  
  
 `/// <reference path="MyService.asmx" />`  
  
 `/// <reference path="Services/MyService.asmx" />`  
  
 `/// <reference path="../MyService.asmx" />`  
  
 `/// <reference path="~/Services/MyService.asmx" />`  
  
> [!NOTE]
>  JavaScript IntelliSense is not supported for script that is contained in Web service (.asmx) files in Web Application Projects (WAP).  
  
 The following example shows how to reference page-based script.  
  
 `/// <reference path="Default.aspx" />`  
  
 `/// <reference path="Admin/Default.aspx" />`  
  
 `/// <reference path="../Default.aspx" />`  
  
 `/// <reference path="~/Admin/Default.aspx" />`  
  
 The following rules apply to a `reference` directive.  
  
-   The `reference` XML comment must be declared before any script.  
  
-   You must use XML comments syntax with three slashes. References made by using standard comments syntax (two slashes) are ignored.  
  
-   Only one file or resource can be specified per directive.  
  
-   Multiple references to page-based scripts are not allowed.  
  
-   If a page reference is specified, no other type of reference directives is allowed.  
  
-   File names use relative paths. You can use the tilde operator (`~`) to make application-root-relative paths.  
  
-   Absolute paths are ignored.  
  
-   Reference directives in referenced pages will not be processed—that is, reference directives are not resolved recursively for pages. Only script that is referenced directly by the page is included.  
  
####  <a name="ReferenceGroups"></a> Reference Groups  
 You can use predefined reference groups to specify that particular IntelliSense .js files are in scope for different JavaScript projects. The following reference group types are available:  
  
-   Implicit (Windows), for Windows 8.x Store apps using JavaScript. Files included in this group are in scope for every .js file opened in the Code Editor for the project of the specified type.  
  
-   Implicit (Web), for HTML5 projects. Files included in this group are in scope for every .js file opened in the Code Editor for these project types.  
  
-   Dedicated worker reference groups, for HTML5 Web Workers. Files specified in this group are in scope for .js files that have an explicit reference to a dedicated worker reference group.  
  
-   Generic, for other JavaScript project types.  
  
 In most scenarios, you don't have to modify reference groups. However, if you want to make changes, you can use configuration options for the JavaScript Code Editor to specify the files included in the reference groups. For instructions about using this feature, see [Options, Text Editor, JavaScript, IntelliSense](../VS_IDE/Options--Text-Editor--JavaScript--IntelliSense.md).  
  
> [!TIP]
>  The IntelliSense references are typically used to provide IntelliSense support for global objects and for IntelliSense [extensions](#Extensibility). You can also use this feature for scripts that must be loaded at runtime using the script loader.  
  
### Remote File References  
 You can instruct Visual Studio to download remote JavaScript files that are referenced in a JavaScript file in order to provide IntelliSense support for the remote file or library. When you use this feature, files will download when you include them as a reference in your JavaScript file.  
  
> [!NOTE]
>  Except for Web projects, this feature works only for JavaScript files that are opened outside the context of a project. For Web projects, remote files referenced in your project are downloaded by default.  
  
 For instructions about using this feature, see [Options, Text Editor, JavaScript, IntelliSense](../VS_IDE/Options--Text-Editor--JavaScript--IntelliSense.md).  
  
> [!WARNING]
>  If you enable this feature and you observe slower performance in the Code Editor, we recommend that you disable it.  
  
###  <a name="XMLDocComments"></a> XML Documentation Comments  
 XML documentation comments are text descriptions of code elements that you add to script. These text descriptions are displayed in IntelliSense when you reference the commented script. For example, you can provide information about a function's parameters and return value. XML documentation comments are available only from referenced files, assemblies, and services. For more information, see [XML Documentation Comments](../VS_IDE/XML-Documentation-Comments--JavaScript-.md) and [Create XML Documentation Comments](../VS_IDE/Create-XML-Documentation-Comments-for-JavaScript-IntelliSense.md).  
  
 IntelliSense can display XML documentation comments in the following scenarios:  
  
-   A .js file that references another .js file.  
  
-   A .js file that references an .aspx file.  
  
-   An .aspx file that references a .js file.  
  
 IntelliSense is not available when one .aspx file references another .aspx file.  
  
###  <a name="ASPNet"></a> ASP.NET AJAX Objects  
 ASP.NET AJAX also supports JavaScript IntelliSense. ASP.NET AJAX includes a client framework that extends the standard types that are available in ECMAScript (JavaScript). To enable JavaScript IntelliSense to provide details about ASP.NET AJAX objects, XML documentation comments have been added throughout the Microsoft Ajax Library. These XML documentation comments are displayed when you use types and members that are contained in the ASP.NET AJAX Library.  
  
> [!NOTE]
>  Private members are not displayed by JavaScript IntelliSense. Private members are denoted in ASP.NET AJAX as members that begin with an underscore (_).  
  
##  <a name="Extensibility"></a> JavaScript IntelliSense Extensibility  
 The JavaScript language service provides objects and functions that enable you to modify the IntelliSense experience for developers who use third-party libraries. These features are especially useful when the default language service isn't able to provide all the information that you want to provide to customers. For more information, see [Extending JavaScript IntelliSense](../VS_IDE/Extending-JavaScript-IntelliSense.md).  
  
##  <a name="Validation"></a> JavaScript Validation  
 JavaScript scripting validation occurs constantly in the background. When Visual Studio detects syntax errors in the JavaScript code, feedback is provided in the following ways:  
  
-   Underlined elements in the editor. Wavy red underlines indicate errors. If you hold the mouse pointer over the error, a tooltip displays the error description.  
  
-   **Error List** window. The **Error List** window displays the error description, the file where the error occurred, the line and column number, and the project. To display the **Error List** window, in the **View** menu, click **Error List**.  
  
-   The Output window shows references that were not loaded.  
  
## See Also  
 [Using IntelliSense](../VS_IDE/Using-IntelliSense.md)   
 [Create XML Documentation Comments](../VS_IDE/Create-XML-Documentation-Comments-for-JavaScript-IntelliSense.md)   
 [Extending JavaScript IntelliSense](../VS_IDE/Extending-JavaScript-IntelliSense.md)   
 [Statement Completion for Identifiers](../VS_IDE/Statement-Completion-for-Identifiers.md)   
 [XML Documentation Comments](../VS_IDE/XML-Documentation-Comments--JavaScript-.md)   
 [About the DHTML Object Model](http://go.microsoft.com/fwlink/?LinkID=92344)   
 [List Members](assetId:///1b9cc469-9cd4-4d42-9999-1f9479635ff8)   
 [SRC Attribute &#124; src Property](http://go.microsoft.com/fwlink/?LinkId=92345)