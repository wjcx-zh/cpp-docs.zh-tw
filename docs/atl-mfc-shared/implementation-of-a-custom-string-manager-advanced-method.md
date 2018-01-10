---
title: "實作的自訂字串管理員 （進階方法） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e76edc65e5f30fee90f346d5434ecbee320a37a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>實作的自訂字串管理員 （進階方法）
在特殊情況下，您可以實作自訂字串管理員不只是變更堆積用來配置記憶體。 在此情況下，您必須以手動方式實作[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)介面做為您的自訂字串管理員。  
  
 若要這樣做，請務必先了解如何[CStringT](../atl-mfc-shared/reference/cstringt-class.md)使用介面來管理其字串資料。 每個執行個體`CStringT`有一個指標指向[CStringData](../atl-mfc-shared/reference/cstringdata-class.md)結構。 此變數長度結構包含重要資訊的字串 （例如長度），以及字串的實際字元資料。 每個自訂字串管理員會負責配置和釋出的要求，這些結構`CStringT`。  
  
 `CStringData`結構包含四個欄位：  
  
-   [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr)此欄位會指向`IAtlStringMgr`用來管理此字串資料的介面。 當`CStringT`需要重新配置或釋放其所呼叫的重新配置或可用的方法，這個介面，傳遞的字串緩衝區`CStringData`結構做為參數。 配置時`CStringData`結構在字串管理員中，您必須設定此欄位，以指向您的自訂字串管理員。  
  
-   [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength)此欄位會包含目前邏輯儲存在緩衝區不包括結束的 null 字串的長度。 `CStringT`此欄位變更時，更新字串的長度。 配置時`CStringData`結構中，字串管理員必須將此欄位設為零。 當重新配置`CStringData`結構，您的自訂字串管理員必須將此欄位保留不變。  
  
-   [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength)此欄位包含字元 （不含結束 null） 可以儲存在此字串緩衝區，且不重新配置它的最大數目。 每當`CStringT`需要增加邏輯字串的長度，它會先檢查此欄位，以確定在緩衝區中沒有足夠的空間。 如果檢查失敗，`CStringT`呼叫您的自訂字串管理員重新配置緩衝區。 配置或重新配置時`CStringData`結構，您必須將此欄位至最少的要求中的字元數**nChars**參數[IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate)或[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)。 如果沒有更多的空間比要求的緩衝區中，您可以設定這個值以反映實際可用的空間量。 這可讓`CStringT`成長來填滿整個字串配置之前必須先呼叫字串管理員，重新配置緩衝區的空間。  
  
-   [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs)此欄位會包含目前的字串緩衝區的參考計數。 如果值是其中一個，則單一執行個體`CStringT`使用緩衝區。 此外，允許執行個體來讀取和修改緩衝區的內容。 如果值為大於 1，多個執行個體`CStringT`可用緩衝區。 因為共用的字元緩衝區，`CStringT`執行個體只能讀取緩衝區的內容。 若要修改其內容，`CStringT`前會先將緩衝區的複本。 如果值為負數，只有一個執行個體`CStringT`使用緩衝區。 在此情況下，緩衝區會被視為已鎖定。 當`CStringT`執行個體所使用的其他執行個體鎖定的緩衝區`CStringT`可能共用緩衝區。 相反地，這些執行個體建立緩衝區的複本操作內容之前。 此外，`CStringT`使用鎖定的緩衝執行個體不會嘗試共用的任何其他緩衝區`CStringT`指派給它的執行個體。 在此情況下，`CStringT`執行個體將另一個字串複製到鎖定的緩衝區。  
  
     配置時`CStringData`結構，您必須設定此欄位，以反映所允許的緩衝區類型中的共用。 對於大部分的實作，這將值設定為其中一個。 這可讓一般寫入時複製共用行為。 不過，如果字串管理員不支援共用字串緩衝區，將此欄位設為鎖定狀態。 這會強制`CStringT`僅執行個體使用這個緩衝區`CStringT`配置給它。  
  
## <a name="see-also"></a>請參閱  
 [使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)

