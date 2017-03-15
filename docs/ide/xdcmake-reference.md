---
title: "XDCMake 參考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xdcmake"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "xdcmake 程式"
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# XDCMake 參考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

xdcmake.exe 是編譯 .xdc 檔案至 .xml 檔案的程式。  .xdc 檔是由每一套原始程式碼的 Visual C\+\+ 編譯器以建立，在原始程式碼以 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 編譯時，和，在原始程式碼檔包含文件註解標記的 XML 標記時。  
  
### 使用 xdcmake.exe 在 Visual Studio 開發環境  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)。  
  
2.  開啟 \[**組態屬性**\] 資料夾。  
  
3.  按一下 \[**XML 文件註解。**\] 屬性頁。  
  
> [!NOTE]
>  在命令列的 xdcmake.exe 選項與選項不同，因為 xdcmake.exe 用於開發環境時 \(屬性頁\)。  如需使用 xdcmake.exe 的資訊在開發環境中，請參閱 [XML 文件產生器工具屬性頁](../ide/xml-document-generator-tool-property-pages.md)。  
  
## 語法  
 xdcmake `input_filename options`  
  
## 參數  
 其中：  
  
 `input_filename`  
 用來當做輸入的 .xdc 檔案的檔名。xdcmake.exe。  指定一或多個 .xdc 檔案或使用 \*.xdc 使用任何 .xdc 檔案是在目前的目錄。  
  
 `options`  
 零或多個下列:  
  
|選項|描述|  
|--------|--------|  
|\/? ， \/help|xdcmake.exe 的顯示說明。|  
|\/assembly:*filename*|在 .xml 檔可讓您指定 \<assembly\> 標記的值。  根據預設， \<assembly\> 標記的值是 .xml 檔的檔名相同。|  
|\/nologo|隱藏著作權訊息。|  
|\/out:*filename*|讓您指定 .xml 檔案的名稱。  根據預設， .xml 檔案的名稱是 xdcmake.exe 處理的第一個 .xdc 檔案的檔名。|  
  
## 備註  
 在建立專案時， Visual Studio 會自動叫用 xdcmake.exe。  您也可以叫用 xdcmake.exe 在命令列。  
  
 請參閱 [文件註解的建議的標記。](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) 。如需將文件註解的更多資訊加入至原始程式碼檔案。  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)