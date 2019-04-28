---
title: CFixedStringT:自訂字串管理員範例
ms.date: 11/04/2016
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
ms.openlocfilehash: 2b6da5d4166b220ef63500d0154ab32dc72b40f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209873"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT:自訂字串管理員範例

ATL 程式庫會實作一個類別所使用的自訂字串管理員範例[CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md)稱為**CFixedStringMgr**。 `CFixedStringT` 衍生自[CStringT](../atl-mfc-shared/reference/cstringt-class.md)並實作的一部分配置其字元資料字串`CFixedStringT`物件本身，只要該字串是所指定的長度小於`t_nChars`的範本參數`CFixedStringT`. 使用此方法時，不需要字串堆積，除非字串的長度超過的固定緩衝區的大小。 因為`CFixedStringT`並非永遠不使用的堆積配置其字串資料，它不能使用`CAtlStringMgr`為其字串管理員。 它會使用自訂字串管理員 (`CFixedStringMgr`)，它會實作[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)介面。 這個介面會討論[的自訂字串管理員實作 （進階方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)。

建構函式`CFixedStringMgr`採用三個參數：

- *pData:* 固定的指標`CStringData`要使用的結構。

- *nChars:* 最大字元數`CStringData`結構可以保存。

- *pMgr:* 指標`IAtlStringMgr`介面的 「 備份字串 manager 」。

建構函式儲存的值*pData*並*pMgr*在其各自的成員變數 (`m_pData`和`m_pMgr`)。 然後，它會設定為零，就會有可用的長度等於最大的大小固定的緩衝區，並為-1 的參考計數的緩衝區的長度。 參考計數值，指出緩衝區已鎖定，並將這個執行個體`CFixedStringMgr`作為字串的經理。

將緩衝區標示為已鎖定可防止其他`CStringT`中保存緩衝區的共用的參考的執行個體。 如果有其他`CStringT`共用它是可行的緩衝區所包含的緩衝區所允許的執行個體`CFixedStringT`其他字串仍持續使用緩衝區時被刪除。

`CFixedStringMgr` 是的完整實作`IAtlStringMgr`介面。 每個方法的實作會分別討論。

## <a name="implementation-of-cfixedstringmgrallocate"></a>CFixedStringMgr::Allocate 的實作

實作`CFixedStringMgr::Allocate`字串的要求的大小是否小於或等於固定緩衝區的大小會先檢查 (儲存在`m_pData`成員)。 如果固定的緩衝區夠大，足以，`CFixedStringMgr`鎖定固定的緩衝區長度為零。 只要字串的長度不超過的固定緩衝區的大小會`CStringT`就不需要重新配置的緩衝區。

如果字串的要求的大小大於固定緩衝區`CFixedStringMgr`要求轉送給字串備份管理員。 備份字串 manager 會假設配置堆積中的緩衝區。 不過，再傳回此緩衝區`CFixedStringMgr`鎖定緩衝區，並以指標取代緩衝區的字串 manager 指標`CFixedStringMgr`物件。 這可確保，嘗試重新配置或釋放緩衝區`CStringT`將會呼叫`CFixedStringMgr`。

## <a name="implementation-of-cfixedstringmgrreallocate"></a>CFixedStringMgr::ReAllocate 的實作

實作`CFixedStringMgr::ReAllocate`非常類似於它的實作`Allocate`。

若要重新配置的緩衝區是固定的緩衝區，要求的緩衝區大小小於固定的緩衝區，不會進行配置。 不過，如果要重新配置不是固定的緩衝區，它必須是以備份管理員所配置的緩衝區。 在此情況下的備份管理員用來重新配置的緩衝區。

如果要重新配置的緩衝區是固定的緩衝區，而且新的緩衝區大小太大而無法容納固定的緩衝區，`CFixedStringMgr`會配置新緩衝區使用的備份管理員。 固定緩衝區的內容之後會複製到新的緩衝區。

## <a name="implementation-of-cfixedstringmgrfree"></a>CFixedStringMgr::Free 的實作

實作`CFixedStringMgr::Free`遵循相同的模式，作為`Allocate`和`ReAllocate`。 如果要釋放的緩衝區是固定的緩衝區，則方法會將它設定為零長度的鎖定緩衝區。 如果要釋放的緩衝區配置與備份管理員、`CFixedStringMgr`釋放它會使用備份管理員。

## <a name="implementation-of-cfixedstringmgrclone"></a>CFixedStringMgr::Clone 的實作

實作`CFixedStringMgr::Clone`永遠會備份管理員傳回的指標而不是`CFixedStringMgr`本身。 這是因為每個執行個體`CFixedStringMgr`只能是單一執行個體相關聯`CStringT`。 其他任何執行個體`CStringT`嘗試進行複製，管理員應該會看到的備份管理員改為。 這是因為共用的備份管理員支援。

## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>CFixedStringMgr::GetNilString 的實作

實作`CFixedStringMgr::GetNilString`傳回固定的緩衝區。 因為一對一的對應`CFixedStringMgr`並`CStringT`，指定的執行個體`CStringT`永遠不會一次使用一個以上的緩衝區。 因此，nil 字串和實際的字串緩衝區永遠不需要在相同的時間。

固定的緩衝區不在使用中，每當`CFixedStringMgr`可確保它長度為零初始化。 這可讓它用做為 nil 的字串。 另外，`nAllocLength`固定緩衝區的成員一律設為完整大小的固定緩衝區。 這表示`CStringT`所能成長的字串，而不會呼叫[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)，即便 nil 的字串。

## <a name="requirements"></a>需求

**標頭：** cstringt.h

## <a name="see-also"></a>另請參閱

[使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)
