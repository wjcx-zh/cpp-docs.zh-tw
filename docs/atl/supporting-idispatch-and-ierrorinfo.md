---
title: 支援 IDispatch 和 IErrorInfo
ms.date: 11/04/2016
f1_keywords:
- IErrorInfo
- IDispatch
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: ea45f0bdd2363f4392baee049629c55259e45af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502423"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>支援 IDispatch 和 IErrorInfo

您可以使用此範本類別[IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供的預設實作`IDispatch Interface`任何物件上的雙重介面的一部分。

如果您的物件會使用`IErrorInfo`介面來報告錯誤傳回至用戶端中，則您的物件必須支援`ISupportErrorInfo Interface`介面。 此範本類別[ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)提供簡單的方法，若要這樣做，如果您只有單一介面產生物件上的錯誤。

## <a name="see-also"></a>另請參閱

[ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)

