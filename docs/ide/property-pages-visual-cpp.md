---
title: "屬性頁 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.NotAProp.Edit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "建置巨集"
  - "巨集, 專案檔"
  - "專案屬性 [C++], 預設值"
  - "專案屬性 [C++], 設定"
  - "專案檔巨集"
  - "屬性頁, 專案設定"
  - "使用者定義巨集"
  - "使用者定義值"
  - "Visual C++ 專案, 屬性"
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 屬性頁 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

藉由使用屬性頁，您可以指定 Visual Studio 專案的設定。  若要開啟 Visual Studio 專案的 \[**屬性頁**\] 對話方塊，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
 您可以指定專案設定，使其套用所有組建組態，或是您可以為每個組建組態指定不同的專案屬性。  例如，您可以指定發行組態的特定設定和偵錯組態的其他設定。  
  
 並非所有可用的頁面都一定會顯示在 \[**屬性頁**\] 對話方塊中。  要顯示的網頁取決於專案中的檔案類型。  
  
 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
## 預設屬性與修改的屬性的比較  
 當您使用 \[**新增專案**\] 對話方塊來建立專案，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 會使用指定的專案範本初始化專案屬性。  因此，在此範本中的屬性值可以視為該專案類型的預設值。  在其他專案類型中，屬性可能會有不同的預設值。  
  
 如果專案屬性值已修改，會顯示為粗體。  專案屬性可能會因為下列原因修改：  
  
-   應用程式精靈變更了屬性，因為它需要的屬性值和專案範本中指定的不同。  
  
-   您在 \[**新增專案**\] 對話方塊中指定不同的屬性值。  
  
-   您在專案屬性頁上指定不同的屬性值。  
  
> [!TIP]
>  若要查看 MSBuild 用來建置您的專案的最後一組屬性值，請檢查前置處理器輸出檔案，您可藉由使用下列命令列產生該檔案：**MSBuild \/preprocess:***preprocessor\_output\_filename*opt *project\_filename*opt  
  
## 重設屬性  
 當您在 \[**屬性頁**\] 對話方塊中檢視專案並在 \[**方案總管**\] 中選取專案節點時，您可以針對許多屬性選取**繼承自父代或專案預設值**或以另一種方式修改值。  
  
 當您在 \[**屬性頁**\] 對話方塊中檢視專案並在 \[**方案總管**\] 中選取檔案時，您可以針對許多屬性選取**繼承自父代或專案預設值**或以另一種方式修改值。  不過，如果專案包含的許多檔案都具有和專案預設值不同的屬性值，建置專案需要較長的時間。  
  
> [!TIP]
>  若要重新整理 \[**屬性頁**\] 對話方塊以顯示最新的選取內容，請按一下 \[**套用**\]。  
  
 大部分的專案預設值為系統 \(平台\) 預設值。  有些專案預設值衍生自樣式表，當您在專案的**一般**組態屬性頁的**專案預設值**區段中更新屬性時可套用這些樣式表。  如需詳細資訊，請參閱[一般屬性頁 \(專案\)](../ide/general-property-page-project.md)。  
  
## 指定使用者定義值  
 您必須定義特定屬性的值。  使用者定義值可以包含一或多個英數字元或專案檔巨集名稱。  其中某些屬性可以只取得一個使用者定義值，但是其他屬性可以取得以分號分隔的多個值清單。  
  
 若要指定屬性的使用者定義值，或是如果屬性可取得多個使用者定義值時指定清單，請在屬性名稱右邊的資料行中，執行下列其中一個動作：  
  
-   輸入值或值的清單。  
  
-   按一下下拉箭號。  如果可以使用 \[**編輯**\]，請按一下它，然後在文字方塊中輸入值或值的清單。  指定清單的替代方式是在文字方塊中的個別行上輸入每個值。  在屬性頁上，這些值將顯示為以分號分隔的清單。  
  
     若要插入專案檔巨集做為值，請按一下 \[**巨集**\]，然後按兩下巨集名稱。  
  
-   按一下下拉箭號。  如果可以使用 \[**瀏覽**\]，請按一下它，然後選取一或多個值。  
  
 對於多重值屬性，當您按一下屬性名稱右邊資料行中的下拉式箭號，然後按一下 \[**編輯**\] 時，即可使用**繼承自父代或專案預設值**選項。  根據預設，這個選項已選取。  
  
 請注意，屬性頁只會為繼承自另一個層級之多重值屬性顯示目前層級的設定。  例如，如果在 \[**方案總管**\] 中選取檔案，而且您選取 C\/C\+\+ **前置處理器定義**屬性，會顯示檔案層級定義，但是不會顯示繼承的專案層級定義。  若要檢視目前層級和繼承的值，請按一下屬性名稱右邊資料行的下拉式箭號，然後按一下 \[**編輯**\]。  如果您使用 [Visual C\+\+ 專案模型](http://msdn.microsoft.com/zh-tw/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f)，這個行為也會影響檔案和專案上的物件。  也就是說，當您在檔案層級查詢屬性上的值，您不會在專案層級收到相同屬性的值。  您必須在專案層級明確取得屬性的值。  此外，屬性的某些繼承值可能來自無法以程式設計方式存取的樣式表。  
  
## 本章節內容  
  
1.  [加入參考搜尋路徑對話方塊](http://msdn.microsoft.com/zh-tw/4520d80d-aa9f-4d11-b92b-2f64a1fd5cb2)  
  
2.  [進階、資訊清單工具、組態屬性、\<Projectname\> 屬性頁對話方塊](../ide/advanced-manifest-tool.md)  
  
3.  [命令列屬性頁](../ide/command-line-property-pages.md)  
  
4.  [自訂建置步驟屬性頁：一般](../ide/custom-build-step-property-page-general.md)  
  
5.  [加入參考](../ide/adding-references-in-visual-cpp-projects.md)  
  
6.  [一般屬性頁 \(檔案\)](../ide/general-property-page-file.md)  
  
7.  [一般屬性頁 \(專案\)](../ide/general-property-page-project.md)  
  
8.  [一般、資訊清單工具、組態屬性、\<Projectname\> 屬性頁對話方塊](../ide/general-manifest-tool-configuration-properties.md)  
  
9. [HLSL 屬性頁](../ide/hlsl-property-pages.md)  
  
10. [HLSL 屬性頁：進階](../ide/hlsl-property-pages-advanced.md)  
  
11. [HLSL 屬性頁：一般](../ide/hlsl-property-pages-general.md)  
  
12. [HLSL 屬性頁：輸出檔](../ide/hlsl-property-pages-output-files.md)  
  
13. [輸入和輸出、資訊清單工具、組態屬性、\<Projectname\> 屬性頁對話方塊](../ide/input-and-output-manifest-tool.md)  
  
14. [隔離的 COM、資訊清單工具、組態屬性、\<Projectname\> 屬性頁對話方塊](../ide/isolated-com-manifest-tool.md)  
  
15. [連結器屬性頁](../ide/linker-property-pages.md)  
  
16. [Managed 資源屬性頁](../ide/managed-resources-property-page.md)  
  
17. [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)  
  
18. [MIDL 屬性頁](../ide/midl-property-pages.md)  
  
19. [MIDL 屬性頁：進階](../ide/midl-property-pages-advanced.md)  
  
20. [MIDL 屬性頁：一般](../ide/midl-property-pages-general.md)  
  
21. [MIDL 屬性頁：輸出](../ide/midl-property-pages-output.md)  
  
22. [NMake 屬性頁](../ide/nmake-property-page.md)  
  
23. [資源屬性頁](../ide/resources-property-pages.md)  
  
24. [VC\+\+ 目錄屬性頁](../ide/vcpp-directories-property-page.md)  
  
25. [Web 參考屬性頁](../ide/web-references-property-page.md)  
  
26. [XML 資料產生器工具屬性頁](../ide/xml-data-generator-tool-property-page.md)  
  
27. [XML 文件產生器工具屬性頁](../ide/xml-document-generator-tool-property-pages.md)  
  
## 請參閱  
 [如何：建立和移除專案相依性](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)   
 [如何：建立和編輯組態](../Topic/How%20to:%20Create%20and%20Edit%20Configurations.md)   
 [部署應用程式](http://msdn.microsoft.com/zh-tw/4ff8881d-0daf-47e7-bfe7-774c625031b4)