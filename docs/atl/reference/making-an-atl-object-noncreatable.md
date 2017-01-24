---
title: "讓 ATL 物件變成無法建立的 | Microsoft Docs"
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
  - "vc.appwiz.ATL.objects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 無法建立的物件"
  - "無法建立的 ATL 物件"
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 讓 ATL 物件變成無法建立的
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可變更 ATL 架構 COM 物件的屬性，使得用戶端無法直接建立物件。  在這種情況下，物件會透過方法呼叫其他物件來傳回而不是直接建立的。  
  
### 若要讓物件變成無法建立的  
  
1.  移除物件的 [OBJECT\_ENTRY\_AUTO](../Topic/OBJECT_ENTRY_AUTO.md)。  如果要使物件變成無法建立的，但要註冊控制項，請用 [OBJECT\_ENTRY\_NON\_CREATEABLE\_EX\_AUTO](../Topic/OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.md) 取代 OBJECT\_ENTRY\_AUTO。  
  
2.  將 [noncreatable](../../windows/noncreatable.md) 屬性加入至 .idl 檔中的 coclass。  例如：  
  
    ```  
    [  
       uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),  
       helpstring("MyObject"),  
      noncreatable  
    ]  
    coclass MyObject  
    {  
       [default] interface IMyInterface;  
    }  
    ```  
  
## 請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [Visual C\+\+ 專案類型](../../ide/visual-cpp-project-types.md)   
 [使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)