---
title: 自訂字串管理員實作 （進階方法） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dd21ffbaf3e3a6654e23346af39ab401484b1cd
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757230"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>自訂字串管理員實作 （進階方法）

在特殊情況下，您可能想要實作不只是變更的堆積來配置記憶體的自訂字串管理員。 在此情況下，您必須以手動方式實作[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)介面做為您的自訂字串管理員。

若要這樣做，請務必先了解如何[CStringT](../atl-mfc-shared/reference/cstringt-class.md)使用該介面來管理其字串資料。 每個執行個體`CStringT`有一個指標指向[CStringData](../atl-mfc-shared/reference/cstringdata-class.md)結構。 此可變長度的結構會包含重要資訊的字串 （例如長度），以及實際的字元資料字串。 每個自訂字串管理員負責配置和釋放的要求，這些結構`CStringT`。

`CStringData`結構包含四個欄位：

- [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr)這個欄位會指向`IAtlStringMgr`用來管理此字串資料的介面。 當`CStringT`需要重新配置或釋放字串緩衝區，它會呼叫重新配置或可用的方法，此介面，並傳遞`CStringData`做為參數的結構。 配置時`CStringData`結構在字串管理員中，您必須設定此欄位，以指向您的自訂字串管理員。

- [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength)此欄位會包含目前邏輯儲存在緩衝區不包括結束的 null 字串的長度。 `CStringT` 字串的長度變更時，請更新此欄位。 配置時`CStringData`結構中，字串管理員必須將此欄位設定為零。 當重新配置`CStringData`結構中，您的自訂字串管理員必須將此欄位保留不變。

- [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength)此欄位包含的字元 （不含終止 null） 可以儲存在這個字串緩衝區，不需要重新配置它的數目上限。 每當`CStringT`需要增加邏輯字串的長度，它會先檢查此欄位，以確定有足夠的空間緩衝區中。 如果檢查失敗，`CStringT`呼叫您的自訂字串管理員以重新配置的緩衝區。 當配置或重新配置`CStringData`結構中，您必須將此欄位到最少的要求中的字元數*nChars*參數來[IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate)或[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)。 如果比要求的緩衝區中有更多空間，您可以設定此值，以反映實際可用的空間量。 這可讓`CStringT`成長以填滿整個字串配置之前必須回呼字串管理員，若要重新配置緩衝區的空間。

- [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs)此欄位會包含目前的字串緩衝區的參考計數。 如果值為 1，則單一執行個體`CStringT`使用緩衝區。 此外，允許的執行個體來讀取和修改緩衝區的內容。 如果值為大於一，多個執行個體`CStringT`可用緩衝區。 因為字元緩衝區共用，`CStringT`執行個體只能讀取緩衝區的內容。 若要修改的內容，`CStringT`首先會建立一份緩衝區。 如果值為負數，只有一個執行個體`CStringT`使用緩衝區。 在此情況下，緩衝區會被視為已鎖定。 當`CStringT`執行個體正在使用的其他執行個體鎖定的緩衝區`CStringT`可能共用緩衝區。 相反地，這些執行個體便會建立一份緩衝區操作內容之前。 颾魤 ㄛ`CStringT`執行個體使用鎖定的緩衝區不會嘗試共用的任何其他緩衝區`CStringT`指派給它的執行個體。 在此情況下，`CStringT`執行個體將另一個字串複製到鎖定的緩衝區。

   配置時`CStringData`結構中，您必須設定此欄位以反映所允許之緩衝區類型中的共用。 對於大部分的實作，這將值設定為其中一個。 這可讓一般的寫入時複製共用行為。 不過，如果字串管理員不支援共用字串緩衝區，設定此欄位設為鎖定狀態。 這會強制`CStringT`僅執行個體中使用這個緩衝區`CStringT`，配置給它。

## <a name="see-also"></a>另請參閱

[使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)

