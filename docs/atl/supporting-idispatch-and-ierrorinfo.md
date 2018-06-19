---
title: 支援 IDispatch 和 IErrorInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94f4c99da3989cce84bd5b6bd3bbfee8df97ff43
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360945"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>支援 IDispatch 和 IErrorInfo
您可以使用此範本類別[IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供的預設實作`IDispatch Interface`任何物件上的雙重介面的一部分。  
  
 如果您的物件使用`IErrorInfo`介面，以報告錯誤傳回至用戶端，則您的物件必須支援`ISupportErrorInfo Interface`介面。 此範本類別[ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)提供簡單的方法，如果您只需要單一的介面，會產生錯誤，在物件上的執行。  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)

