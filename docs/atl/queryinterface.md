---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: 37bb7a8c7fef963f340704561e24e33cc36707f3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298632"
---
# <a name="queryinterface"></a>QueryInterface

雖然物件可以表達其以靜態方式提供的功能（在具現化之前），但基本 COM 機制是使用稱為[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))的 `IUnknown` 方法。

每個介面都衍生自 `IUnknown`，因此每個介面都有 `QueryInterface`的執行。 不論是否執行，這個方法都會使用呼叫端想要指標的介面的 IID 來查詢物件。 如果物件支援該介面，`QueryInterface` 會抓取介面的指標，同時也會呼叫 `AddRef`。 否則，它會傳回 E_NOINTERFACE 的錯誤碼。

請注意，您必須遵守所有時間的[參考計數](../atl/reference-counting.md)規則。 如果您在介面指標上呼叫 `Release`，以將參考計數遞減為零，則不應該再次使用該指標。 有時候您可能需要取得物件的弱式參考（也就是，您可能想要取得其中一個介面的指標，而不遞增參考計數），但藉由呼叫後面接著 `Release`的 `QueryInterface`，就無法接受。 以這種方式取得的指標無效，因此不應使用。 當定義[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)時，這會變得很明顯，因此定義此宏是尋找參考計數錯誤的實用方式。

## <a name="see-also"></a>請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[QueryInterface：在物件中流覽](/windows/win32/com/queryinterface--navigating-in-an-object)
