---
title: "/GA (針對 Windows 應用程式最佳化) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication"
  - "/ga"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GA 編譯器選項 [C++]"
  - "GA 編譯器選項 [C++]"
  - "-GA 編譯器選項 [C++]"
  - "Windows 最佳化編譯器選項"
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GA (針對 Windows 應用程式最佳化)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會針對 .exe 檔案產生可更有效率存取執行緒區域儲存區 \(Thread Local Storage，TLS\) 變數的程式碼。  
  
## 語法  
  
```  
/GA  
```  
  
## 備註  
 **\/GA** 會加速存取 Windows 架構程式中以 [\_\_declspec\(thread\)](../../cpp/declspec.md) 宣告的資料。  設定這個選項之後，[\_\_tls\_index](http://msdn.microsoft.com/library/windows/desktop/ms686749) 巨集會被假設為 0。  
  
 對 DLL 使用 **\/GA** 會導致錯誤程式碼的產生。  
  
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