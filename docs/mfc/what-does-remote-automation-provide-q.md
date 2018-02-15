---
title: "Remote Automation 提供什麼功能？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Remote Automation, DCOM
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4a82b26a1e6c208a584dfd19ebfd4530b4bdf76
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="what-does-remote-automation-provide"></a>Remote Automation 提供什麼功能？
Remote Automation 可讓程式在各部電腦間叫用 `IDispatch` 實作。 它也支援 Automation 所需，特別是其他介面**IEnumVARIANT**集合支援。 不提供散發任何其他 COM 介面的功能 (除了**IUnknown**當然) 而且像一般 Automation，包含只針對 Automation 支援的這些資料類型的封送處理支援。  
  
 這套工具可讓程式存取方法和屬性，包括在可存取的網路節點上執行之物件的傳回集合或更進一步自動化物件。 如果用戶端電腦也執行適當的軟體，就可再次使用 Automation 功能 (此僅適用於 32 位元和 64 位元用戶端，並且在概念上類似事件，不過它不會使用相同機制)，讓伺服器回呼至用戶端。  
  
 對於可操作為 Remote Automation 伺服器的應用程式，則必須實作為可執行檔 (即為「本機伺服器」而不是「inproc 伺服器」)。  
  
## <a name="see-also"></a>請參閱  
 [沒有 Remote Automation 適用於什麼情況](where-does-remote-automation-fit-in-q.md)   
 [DCOM 的歷史](../mfc/history-of-dcom.md)
