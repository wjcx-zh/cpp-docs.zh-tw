---
title: "啟用和停用提供者的服務 | Microsoft Docs"
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
  - "OLE DB 服務 [OLE DB], 啟用和停用"
  - "服務提供者 [OLE DB]"
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 啟用和停用提供者的服務
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可為存取單一提供者的所有應用程式，將個別的 OLE DB 服務預設成啟用或停用。  這是透過在提供者的 CLSID 底下加入 **OLEDB\_SERVICES** 登錄項目而達成的，而 `DWORD` 數值則指定要啟用或停用的服務，如下所示：  
  
|啟用的預設服務|關鍵字的值|  
|-------------|-----------|  
|所有服務 \(預設值\)|0xffffffff|  
|Pooling 和 AutoEnlistment 以外的所有服務|0xfffffffe|  
|Client Cursor 以外的所有服務|0xfffffffb|  
|Pooling、AutoEnlistment 和 Client Cursor 以外的所有服務|0xfffffff0|  
|無服務|0x00000000|  
|無彙總，所有服務都停用|\<遺漏索引鍵\>|  
  
## 請參閱  
 [啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)