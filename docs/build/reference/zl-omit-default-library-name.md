---
title: "/Zl (省略預設程式庫名稱) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zi"
  - "VC.Project.VCCLCompilerTool.OmitDefaultLibName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zl 編譯器選項 [C++]"
  - "預設程式庫, 省略名稱"
  - "省略預設程式庫名稱編譯器選項"
  - "ZI 編譯器選項"
  - "-Zl 編譯器選項 [C++]"
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /Zl (省略預設程式庫名稱)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 .obj 檔中省略預設的 C 執行階段程式庫名稱。  編譯器是預設為將程式庫名稱置入 .obj 檔案中，以便指引連結器到正確的程式庫。  
  
## 語法  
  
```  
/Zl  
```  
  
## 備註  
 如需有關預設程式庫的詳細資訊，請參閱[使用 Run\-Time 程式庫](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
 您可以使用 **\/Zl** 編譯您打算置入程式庫的 .obj 檔案。  雖然對於單一 .obj 檔案省略程式庫名稱只能節省很少量的空間，但是對於含有許多物件模組的程式庫，總計節省下來的空間就相當可觀了。  
  
 這是進階的選項。  設定這個選項會移除您的應用程式可能需要的特定 C 執行階段程式庫支援，如果您的應用程式依賴這項支援，結果就會造成連結時間錯誤。  如果您使用這個選項，則必須以其他方式提供所需的元件。  
  
 請使用[\/NODEFAULTLIB \(忽略程式庫\)](../../build/reference/nodefaultlib-ignore-libraries.md)指引連結器忽略所有 .obj 檔案中的程式庫參考。  
  
 如需詳細資訊，請參閱[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
 以 **\/Zl** 編譯時，會定義 `_VC_NODEFAULTLIB`。例如：  
  
```  
// vc_nodefaultlib.cpp  
// compile with: /Zl  
void Test() {  
   #ifdef _VC_NODEFAULTLIB  
      int i;  
   #endif  
  
   int i;   // C2086  
}  
```  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**進階**\] 屬性頁。  
  
4.  修改 \[**省略預設程式庫名稱**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)