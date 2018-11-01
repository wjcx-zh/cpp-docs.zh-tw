---
title: ATL 和無限制執行緒封送處理器
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: b9baff9af10cd785554e849854556a9aa3bd7ca4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621841"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL 和無限制執行緒封送處理器

[ATL 簡單物件精靈] 的 [屬性] 頁面上提供選項，可讓您彙總無限制執行緒封送處理器 (FTM) 的類別。

精靈會產生程式碼，以建立可用的執行緒封送處理器中的執行個體`FinalConstruct`並在該執行個體釋放`FinalRelease`。 COM_INTERFACE_ENTRY_AGGREGATE 巨集自動加入到 COM 對應，以確保`QueryInterface`要求[IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal)無限制執行緒封送處理器所處理。

無限制執行緒封送處理器可以直接存取物件的介面從任何執行緒在相同的程序，加速跨 apartment 呼叫。 此選項適用於使用這兩個執行緒模型的類別。

使用此選項時，類別必須負責其資料的執行緒安全。 此外，彙總無限制執行緒封送處理器，而且需要使用從其他物件中取得的介面指標的物件必須採取額外步驟以確保介面會正確地封送處理。 通常這牽涉到將介面指標儲存在全域介面表 (GIT)，然後是每次從 GIT 取得滑鼠指標。 ATL 提供類別[CComGITPtr](../atl/reference/ccomgitptr-class.md)可協助您使用儲存在 GIT 中的介面指標。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/desktop/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal)<br/>
[使用全域介面資料表的時機](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[處理序中的執行緒問題的伺服器](/windows/desktop/com/in-process-server-threading-issues)

