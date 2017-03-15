---
title: "與 C 語言應用程式開發介面的關聯性 | Microsoft Docs"
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
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "書籍 [C++]"
  - "書籍 [C++], 關於 MFC 和 Windows SDK"
  - "MFC [C++], Windows 應用程式開發介面"
  - "Visual C, Windows 應用程式開發介面呼叫"
  - "Windows API [C++], 與 MFC"
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 與 C 語言應用程式開發介面的關聯性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於 Windows，區隔 Microsoft Foundation Class \(MFC\) 程式庫與其他程式庫的一個特點為，以 C 語言撰寫的、對於 Windows 應用程式開發介面非常接近的對應。  此外，您可以自由將對類別庫的呼叫與直接對 Windows API 的呼叫混合在一起。  然而，這種直接存取，並不表示類別可以完整取代應用程式開發介面。  開發人員仍然必須對某些 Windows 函式直接呼叫，例如 [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) 和 [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385)。  只有在有明顯的好處時， Windows 函式會由類別成員函式包裝。  
  
 由於您有時必須呼叫原生 Windows 函式呼叫，您應該存取 C 語言 Windows 應用程式開發介面的文件。  這個檔案包含在 Microsoft Visual C\+\+。  
  
> [!NOTE]
>  如需 MFC 程式庫架構作業的概觀，請參閱 [使用類別撰寫 Windows 的應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)。  
  
## 請參閱  
 [一般類別設計原理](../mfc/general-class-design-philosophy.md)