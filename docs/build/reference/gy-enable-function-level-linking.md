---
title: "/Gy (啟用函式階層連結) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking"
  - "/gy"
  - "VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gy 編譯器選項 [C++]"
  - "COMDAT 函式"
  - "啟用函式階層連結編譯器選項 [C++]"
  - "Gy 編譯器選項 [C++]"
  - "-Gy 編譯器選項 [C++]"
  - "封裝函式"
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Gy (啟用函式階層連結)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讓編譯器以封裝函式 \(COMDATs\) 的格式封裝個別的函式。  
  
## 語法  
  
```  
/Gy[-]  
```  
  
## 備註  
 連結器要求各個函式個別地包裝為 COMDAT，以排除或排序 DLL 或 .exe 檔案中的個別函式。  
  
 您可以使用連結器選項 [\/OPT \(最佳化\)](../../build/reference/opt-optimizations.md)，從 .exe 檔案中排除未參考的封裝函式。  
  
 您可以使用連結器選項 [\/ORDER \(依順序置放函式\)](../../build/reference/order-put-functions-in-order.md)，以指定的順序將封裝函式包含在 .exe 檔案中。  
  
 如果內嵌函式已執行個體化為呼叫 \(發生於內嵌已關閉或您取得函式位址等情況\)，就一定會封裝這些函式。  此外，在類別宣告 \(Class Declaration\) 內定義的 C\+\+ 成員函式也會自動封裝；其他函式則不會，而且必須選取這個選項將它們編譯為封裝函式。  
  
> [!NOTE]
>  用於 \[編輯後繼續\] 的 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 選項會自動設定 **\/Gy** 選項。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**程式碼產生**\] 屬性頁。  
  
4.  修改 \[**啟用函式階層連結**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)