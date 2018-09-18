---
title: QueryInterface |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c361bc9510c610f2004af9f09c061d6f4b8b8cd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057442"
---
# <a name="queryinterface"></a>QueryInterface

不過有些的機制的物件可以用來表示靜態 （它具現化之前），它所提供的功能，是使用基本的 COM 機制`IUnknown`方法呼叫[QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))。

每個介面衍生自`IUnknown`，因此每個介面的實作`QueryInterface`。 不論實作，這個方法會查詢物件使用呼叫端想要的指標之介面的 IID。 如果物件支援該介面，`QueryInterface`擷取介面的指標，同時呼叫`AddRef`。 否則，它會傳回 E_NOINTERFACE 錯誤程式碼。

請注意，您必須遵守[參考計數](../atl/reference-counting.md)隨時的規則。 如果您呼叫`Release`遞減參考計數為零的介面指標，您應該使用該指標一次。 有時候您可能需要取得物件的弱式參考 （也就是您可能想要取得其中一個介面的指標，而不會遞增參考計數），但不是要執行此呼叫可接受`QueryInterface`後面接著`Release`。 以此方式取得的指標無效，而且不應該使用。 這樣更容易變得顯而易見的時機[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)定義，所以定義這個巨集是尋找參考計數錯誤的一種方式。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[瀏覽物件中的 QueryInterface:](/windows/desktop/com/queryinterface--navigating-in-an-object)

