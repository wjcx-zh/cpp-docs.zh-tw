---
title: "CUserException Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CUserException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserException class"
  - "錯誤 [C++], 截獲"
  - "例外狀況, 擲回"
  - "operations [C++]"
  - "operations [C++], 停止"
  - "擲回例外狀況, stopping user operations"
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUserException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擲回阻止使用者作業。  
  
## 語法  
  
```  
class CUserException : public CSimpleException  
```  
  
## 備註  
 要為應用程式特定的例外狀況時，使用擲回或攔截例外狀況機制使用 `CUserException` 。「  使用者」類別名稱可以解譯我的使用者做出我需要處理例外的事」。  
  
 在呼叫 `CUserException` 全域函式之後 `AfxMessageBox` 通知使用者通常會擲回作業失敗。  當您撰寫例外處理常式 \(Exception Handler\) 時，請特別處理例外狀況，因為使用者已經通常會告知已失敗。  架構會在特定情況下擲回這個例外狀況。  要擲回 `CUserException` 警告使用者，然後呼叫全域函式 `AfxThrowUserException`。  
  
 在下列範例中，會包含可能失敗警示使用者並擲回 `CUserException`作業的函式。  呼叫的函式會特別地攔截例外狀況並處理它:  
  
 [!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/CPP/cuserexception-class_1.cpp)]  
  
 如需使用 `CUserException`的詳細資訊，請參閱本文 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [AfxMessageBox](../Topic/AfxMessageBox.md)   
 [AfxThrowUserException](../Topic/AfxThrowUserException.md)   
 [如何?:建立自己的自訂例外狀況類別?](http://go.microsoft.com/fwlink/?LinkId=128045)