---
title: "/V (版本號碼) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/v"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/V 編譯器選項 [C++]"
  - "嵌入版本字串"
  - "V 編譯器選項 [C++]"
  - "-V 編譯器選項 [C++]"
  - "版本編號, 為 .obj 指定"
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /V (版本號碼)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將文字字串嵌入 .obj 檔案中。  已取代。  
  
## 語法  
  
```  
/Vstring  
```  
  
## Arguments  
 `string`  
 要嵌入 .obj 檔案中指定版本號碼或著作權聲明的字串。  
  
## 備註  
 這個字串可以在 .obj 檔案標示版本號碼或著作權聲明。  任何空格或 Tab 字元如果是字串的一部分，都必須以雙引號 \("\) 括住。  任何雙引號標記如果是字串的一部分，前面必須加上反斜線 \(\\\)。  **\/V** 與 `string` 之間的空格是選擇性的。  
  
 您也可以使用 [註解](../../preprocessor/comment-c-cpp.md) 配合編譯器註解型別引數，將編譯器的名稱和版本號碼置入 .obj 檔案中。  
  
 **\/V** 已被取代；**\/V** 主要是用來支援虛擬裝置驅動程式 \(VxD\) 的建置，而 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 工具組已不再支援 VxD 的建置。  如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)