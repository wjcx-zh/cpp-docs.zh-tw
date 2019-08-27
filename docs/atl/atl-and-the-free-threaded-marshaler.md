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
ms.openlocfilehash: 94e4961c69e9441d160d72d9b72afcee3677e25f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491918"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL 和無限制執行緒封送處理器

ATL 簡單物件 Wizard 的 [屬性] 頁面會提供選項, 讓您的類別匯總免費的執行緒封送處理器 (FTM)。

此 wizard 會產生程式碼, 以在中`FinalConstruct`建立免費執行緒封送處理器的實例, 並在中`FinalRelease`釋放該實例。 COM_INTERFACE_ENTRY_AGGREGATE 宏會自動加入至 COM 對應, 以確保`QueryInterface` [IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)的要求是由免費的執行緒封送處理器所處理。

無限制執行緒封送處理器可讓您從相同進程中的任何執行緒直接存取物件上的介面, 加速跨公寓呼叫。 此選項適用于使用這兩個執行緒模型的類別。

使用此選項時, 類別必須負責其資料的執行緒安全。 此外, 匯總無限制執行緒封送處理器並需要使用從其他物件取得之介面指標的物件, 必須採取額外的步驟, 以確保介面已正確封送處理。 通常這牽涉到將介面指標儲存在全域介面表 (GIT) 中, 並在每次使用時從 GIT 取得指標。 ATL 提供類別[CComGITPtr](../atl/reference/ccomgitptr-class.md) , 可協助您使用儲存在 GIT 中的介面指標。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/win32/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)<br/>
[使用全域介面資料表的時機](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[同進程伺服器執行緒問題](/windows/win32/com/in-process-server-threading-issues)
