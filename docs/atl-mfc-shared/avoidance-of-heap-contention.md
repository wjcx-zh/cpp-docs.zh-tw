---
title: 避免堆積競爭
ms.date: 11/04/2016
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
ms.openlocfilehash: c28e5ba01cc2bb1e3cae19087a67cf97e6ac415f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536782"
---
# <a name="avoidance-of-heap-contention"></a>避免堆積競爭

由 MFC 和 ATL 提供的預設字串管理員會在全域的堆積上的簡單包裝函式。 這個全域的堆積會是完整的安全執行緒，這表示，多個執行緒可以配置和釋放記憶體從它同時而不損毀堆積。 為了提供安全執行緒，堆積已序列化至其本身的存取。 這通常被完成的重要區段或類似的鎖定機制。 只要兩個執行緒嘗試同時存取的堆積，一個執行緒會封鎖直到另一個執行緒的要求已完成。 對於許多應用程式，很少會發生這種情況，並在堆積的鎖定機制的效能影響是微不足道。 不過，應用程式經常從多個執行緒存取的堆積堆積的鎖定爭用會造成應用程式的執行速度比如果它是單一執行緒 （即使在有多個 Cpu 的電腦） 上。

使用應用程式[CStringT](../atl-mfc-shared/reference/cstringt-class.md)特別容易堆積競爭因為作業`CStringT`物件經常需要字串緩衝區的配置。

減少堆積競爭執行緒之間的一種方法是將私用的執行緒本機堆積中配置字串的每個執行緒。 只要使用配置的字串在特定執行緒的配置器僅用於該執行緒，配置器不一定要是安全執行緒。

## <a name="example"></a>範例

下列範例說明會在該執行緒上的字串使用它自己私用非安全執行緒的堆積配置的執行緒程序：

[!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]

## <a name="comments"></a>註解

無法使用這個相同的執行緒程序執行多個執行緒，但因為每個執行緒都有它自己的堆積沒有執行緒之間沒有爭用的情況。 此外，每個堆積都不是安全執行緒的事實提供明顯提升效能，即使只有一個執行緒的複本正在執行。 這是堆積，以防止並行存取不用耗費資源的連鎖的作業的結果。

更複雜的執行緒程序中，可能會方便將執行緒的字串管理員的指標儲存在執行緒區域儲存區 (TLS) 位置。 這可讓其他執行緒程序，若要存取執行緒的字串管理員所呼叫的函式。

## <a name="see-also"></a>另請參閱

[使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)

