---
title: "國際化策略 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字元集 [C++], 國際化程式設計策略"
  - "全球化 [C++], 字元集"
  - "可移植的語言程式碼 [C++]"
  - "當地語系化 [C++], 字元集"
  - "MBCS [C++], 國際化策略"
  - "Unicode [C++], 全球化應用程式"
  - "Win32 [C++], 國際化程式設計策略"
  - "Windows API [C++], 國際化程式設計策略"
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 國際化策略
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據目標作業系統和市場而定，您有數種國際化策略：  
  
-   您的應用程式使用 Unicode，因此會執行於 Windows 2000 和 Windows NT，但不能在 Windows 95 或 Windows 98 上執行。  
  
     您使用了 Unicode 特定功能，且所有字元都是 16 位元寬 \(雖然您可以因為特殊目的而在部分程式中使用 ANSI 字元\)。  C 執行階段程式庫可以提供僅用 Unicode 設計程式的函式、巨集和資料型別。  MFC 完全支援 Unicode。  
  
-   您的應用程式使用 MBCS，並且可以在任何的 Win32 平台上執行。  
  
     您使用的是 MBCS 特定功能。  字串可以包含單一位元組字元、雙位元組字元或兩者。  C 執行階段程式庫可以提供僅用 MBCS 設計程式的函式、巨集和資料型別。  MFC 完全支援 MBCS。  
  
-   您的應用程式原始程式碼是為了完整的移植性而撰寫─藉著以 **\_UNICODE** 符號或所定義的 **\_MBCS**  符號重新編譯，您可以產生使用任何一者的版本。  如需詳細資訊，請參閱 [TCHAR.H 裡泛用文字的對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   您的應用程式可以在 Windows 95、Windows 98 和 Windows ME 上使用包裝函式 \(Wrapper Function\) 程式庫來因應遺失的 Unicode 函式，如同在[設計在 Windows 98 和 Windows 2000 上執行的單一 Unicode 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=250770) 中所說明的情況。  包裝函式程式庫也可以商業途徑購買取得。  
  
     您使用的是完全可移植的 C 執行階段函式、巨集和資料型別。  MFC 的彈性支援這些策略的任一個。  
  
 這些主題的其餘部分專注於撰寫可建置為 Unicode 或 MBCS 的完全可移植的程式碼。  
  
## 請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [地區設定和字碼頁](../text/locales-and-code-pages.md)