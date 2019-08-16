---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: de2762cff3d697261e159336d866a5a7cb10fafa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492009"
---
# <a name="queryinterface"></a>QueryInterface

雖然物件可以表達其以靜態`IUnknown`方式提供的功能 (在具現化之前), 但基本 COM 機制是使用稱為[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))的方法。

每個介面都是`IUnknown`衍生自, 因此每個介面都`QueryInterface`有的執行。 不論是否執行, 這個方法都會使用呼叫端想要指標的介面的 IID 來查詢物件。 如果物件支援該介面, `QueryInterface`則會抓取介面的指標, 同時也會呼叫。 `AddRef` 否則, 它會傳回 E_NOINTERFACE 錯誤碼。

請注意, 您必須遵守所有時間的[參考計數](../atl/reference-counting.md)規則。 如果您在`Release`介面指標上呼叫, 將參考計數遞減為零, 則不應該再次使用該指標。 有時候您可能需要取得物件的弱式參考 (也就是, 您可能想要取得其中一個介面的指標, 而不遞增參考計數), 但是藉由呼叫`QueryInterface`後面的`Release`來執行此動作並不可行。 以這種方式取得的指標無效, 因此不應使用。 當定義[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)時, 這會變得很明顯, 因此定義此宏是尋找參考計數錯誤的實用方式。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[QueryInterface在物件中流覽](/windows/win32/com/queryinterface--navigating-in-an-object)
