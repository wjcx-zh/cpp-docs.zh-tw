---
title: "建立提供者 | Microsoft Docs"
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
  - "OLE DB 提供者, 建立"
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

#### 若要以 ATL OLE DB 提供者精靈建立 OLE DB 提供者  
  
1.  在該專案上按一下右鍵。  
  
2.  在捷徑功能表中按一下 \[加入\]，然後按一下 \[加入類別\]。  
  
3.  在 \[加入類別\] 對話方塊中選取 \[ATL OLEDB 提供者\] 圖示，然後按一下 \[開啟\]。  
  
4.  在 ATL OLE DB 提供者精靈的 \[**簡短名稱**\] 方塊中輸入提供者的簡短名稱。  下列主題使用簡短名稱 "MyProvider"，但您可使用其他名稱。  其他的名稱方塊則根據您輸入的名稱來填入 \(Populate\)。  
  
5.  必要時可編輯其他名稱方塊。  您除了物件和檔案名稱，還可編輯下列項目：  
  
    -   **Coclass**：COM 用來建立提供者的名稱  
  
    -   **ProgID**：程式設計識別項，這是可取代 GUID 的文字字串  
  
    -   **Version**：可與 ProgID 和 coclass 一起使用來產生與版本相關的程式 ID  
  
6.  按一下 \[**完成**\]。  
  
## 請參閱  
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)