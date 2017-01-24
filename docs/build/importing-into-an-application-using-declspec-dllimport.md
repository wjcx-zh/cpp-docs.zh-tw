---
title: "使用 __declspec(dllimport) 匯入至應用程式 | Microsoft Docs"
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
  - "__declspec"
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) 關鍵字 [C++]"
  - "匯入 DLL [C++], __declspec(dllimport)"
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 __declspec(dllimport) 匯入至應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 DLL 定義的公用符號之程式可以匯入這些符號。  在建立使用您的 DLL 所建置的應用程式標頭檔時，請在公用符號的宣告上使用 **\_\_declspec\(dllimport\)**。  無論您是使用 .def 檔或 **\_\_declspec\(dllexport\)** 關鍵字來匯出，關鍵字 **\_\_declspec\(dllimport\)** 都可以使用。  
  
 若要使程式碼更好讀取，請定義 **\_\_declspec\(dllimport\)** 的巨集，接著再使用這個巨集來宣告每個匯入符號：  
  
```  
#define DllImport   __declspec( dllimport )  
  
DllImport int  j;  
DllImport void func();  
```  
  
 **\_\_declspec\(dllimport\)** 在函式宣告上是可選擇性地使用，但是如果您使用了這個關鍵字，編譯器會產生更有效率的程式碼。  然而，為了要讓匯入 DLL 的可執行檔可以存取 DLL 的公用資料符號和物件，您必須使用 **\_\_declspec\(dllimport\)**。  請注意，您的 DLL 的使用者仍然需要連結到匯入程式庫。  
  
 您可以對 DLL 和用戶端應用程式使用相同的標頭檔。  若要進行這項作業，請使用特殊的前置處理器符號，指示您要建置 DLL 或建置用戶端應用程式。  例如：  
  
```  
#ifdef _EXPORTING  
   #define CLASS_DECLSPEC    __declspec(dllexport)  
#else  
   #define CLASS_DECLSPEC    __declspec(dllimport)  
#endif  
  
class CLASS_DECLSPEC CExampleA : public CObject  
{ ... class definition ... };  
```  
  
## 您想要執行甚麼工作？  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## 請參閱  
 [匯入至應用程式](../build/importing-into-an-application.md)