---
title: 支援 IDispatch 和 IErrorInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f39db3e844df884e8e95352bed2a078b01beede8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>支援 IDispatch 和 IErrorInfo
您可以使用此範本類別[IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供的預設實作`IDispatch Interface`任何物件上的雙重介面的一部分。  
  
 如果您的物件使用`IErrorInfo`介面，以報告錯誤傳回至用戶端，則您的物件必須支援`ISupportErrorInfo Interface`介面。 此範本類別[ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)提供簡單的方法，如果您只需要單一的介面，會產生錯誤，在物件上的執行。  
  
## <a name="see-also"></a>請參閱  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)

