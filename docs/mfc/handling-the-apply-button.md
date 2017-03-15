---
title: "處理套用按鈕 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "屬性工作表中的套用按鈕"
  - "屬性工作表, 套用按鈕"
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 處理套用按鈕
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

屬性工作表具有標準對話方塊不的功能:它們可讓使用者將變更他們在關閉屬性工作表之前完成。  使用應用程式按鈕，來完成。  本文將討論您可以使用正確實作這項功能的方法。  
  
 當使用者按一下確定關閉對話方塊時，強制回應對話方塊通常將設定套用至外部物件。  這也適用於屬性工作表:當使用者按一下確定時，在屬性工作表的新設定生效。  
  
 不過，您可能想要讓使用者儲存設定，而不需關閉屬性工作表對話方塊。  這是新應用程式的函式。  狀態的新應用程式所有頁面的目前設定屬性頁對外部物件，其中含有目前作用中的網頁的目前設定相對。  
  
 根據預設，應用程式按鈕永遠都會停用。  您必須撰寫程式碼以啟用應用程式按鈕在適當的時間，因此，您必須撰寫程式碼實作應用程式的角色，如下所述。  
  
 如果您不想為使用者提供應用程式功能，移除應用程式按鈕是不必要的。  您可以將它停用，在視窗未來的版本使用標準屬性工作表支援可用的應用程式中常見的。  
  
 報告頁面中修改和啟用應用按鈕，呼叫 **CPropertyPage::SetModified\( TRUE \)**。  如果任何網頁報告被修改，應用按鈕會保持啟用，不論是否已修改目前作用中的網頁。  
  
 您應該呼叫 [CPropertyPage::SetModified](../Topic/CPropertyPage::SetModified.md) ，每當使用者變更網頁上的任何設定。  一種偵測使用者何時變更網頁的設定將實作變更每個告知處理常式在屬性頁的控制項，例如 **EN\_CHANGE** 和 **BN\_CLICKED**。  
  
 若要實作新應用程式的角色，屬性工作表必須呼叫它的擁有人，或者其他外部物件在應用程式，則會使用目前設定屬性頁。  同時，屬性工作表也應該呼叫套用到外部物件的修改的所有網頁的 **CPropertyPage::SetModified\( FALSE \)** 停用應用程式按鈕。  
  
 如需這個程序的範例，請參閱 MFC 一般 [PROPDLG](../top/visual-cpp-samples.md)範例。  
  
## 請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)