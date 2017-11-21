---
title: "實作 CComObjectRootEx |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CComObjectRootEx
dev_langs: C++
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 960f7989d3891be4cf23ef75b0982a2577f5e95e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-ccomobjectrootex"></a>實作 CComObjectRootEx
[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)很重要的; 所有 ATL 物件必須都有一個執行個體`CComObjectRootEx`或[CComObjectRoot](../atl/reference/ccomobjectroot-class.md)在其繼承中。 `CComObjectRootEx` 提供以 COM 對應項目為基礎的預設 `QueryInterface` 機制。  
  
 透過其 COM 對應，當用戶端查詢介面時，物件的介面會公開給用戶端。 查詢是透過 `CComObjectRootEx::InternalQueryInterface` 執行。 `InternalQueryInterface` 只處理 COM 對應表格中的介面。  
  
 您可以將介面輸入到 COM 對應表格[COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry)巨集，或其中一個變數。 例如，下列程式碼會將介面 `IDispatch`、`IBeeper` 和 `ISupportErrorInfo` 輸入到 COM 對應表格：  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)   
 [COM 對應巨集](../atl/reference/com-map-macros.md)

