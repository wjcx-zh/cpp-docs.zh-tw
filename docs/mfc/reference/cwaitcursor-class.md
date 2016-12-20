---
title: "CWaitCursor Class | Microsoft Docs"
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
  - "CWaitCursor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "游標, wait cursor"
  - "CWaitCursor class"
  - "wait cursors"
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWaitCursor Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供了一條線的方式顯示等待游標，通常會顯示為沙漏，反之，因為您正在執行耗時作業。  
  
## 語法  
  
```  
class CWaitCursor  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWaitCursor::CWaitCursor](../Topic/CWaitCursor::CWaitCursor.md)|`CWaitCursor` 建構物件並顯示等待游標。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWaitCursor::Restore](../Topic/CWaitCursor::Restore.md)|在變更之後，還原等待游標它。|  
  
## 備註  
 `CWaitCursor` 不具有基底類別。  
  
 程式設計實務的好視窗需要顯示等待游標，每當您執行花不少時間的作業。  
  
 若要顯示等待游標，請在執行耗時作業的程式碼之前定義 `CWaitCursor` 變數。  物件的建構函式會自動使等待游標隨即顯示。  
  
 當物件超出範圍 \( `CWaitCursor` 物件宣告\) 的區塊結尾，其解構函式會將游標設定為先前游標。  換句話說，物件會自動執行必要的清除。  
  
> [!NOTE]
>  由於其建構函式和解構函式 \(Destructor\) 如何運作， `CWaitCursor` 物件永遠宣告為區域變數 \(但不是宣告為全域變數也不會配置使用 **new**。  
  
 如果您執行可能會使游標會變更，例如顯示訊息方塊或  對話方塊中的作業，請呼叫成員函式 [還原](../Topic/CWaitCursor::Restore.md) 還原等待游標。  即使等待游標目前顯示，可以呼叫 **還原** 。  
  
 可能是另一種顯示等待游標會使用 [CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md)、 [CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md)和 [CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md)的組合。  不過， `CWaitCursor` 更容易使用，因為您不必設定游標至先前游標，在完成長時間作業時。  
  
> [!NOTE]
>  使用 [CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md) 虛擬函式， MFC 會設定並還原游標。  您可以覆寫此函式提供自訂行為。  
  
## 繼承階層架構  
 `CWaitCursor`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 範例  
 [!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/CPP/cwaitcursor-class_1.cpp)]  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md)   
 [CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md)   
 [CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md)   
 [CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md)   
 [如何?:變更 Microsoft Foundation Class 應用程式的滑鼠游標?](http://go.microsoft.com/fwlink/?LinkID=128044)