---
title: ATL 和無限制執行緒封送處理器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1716985adf65b714a418f20d3873f45c32d368b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355822"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL 和無限制執行緒封送處理器
ATL 簡單物件精靈的 [屬性] 頁面上提供選項，可讓您彙總無限制執行緒封送處理器 (FTM) 的類別。  
  
 精靈會產生程式碼來建立執行個體中無限制執行緒封送處理器`FinalConstruct`，並釋放該執行個體中的`FinalRelease`。 A`COM_INTERFACE_ENTRY_AGGREGATE`巨集自動加入到 COM 對應，以確保`QueryInterface`要求[IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)無限制執行緒封送處理器所處理。  
  
 無限制執行緒封送處理器可直接存取物件上的介面相同的程序中的任何執行緒從加速跨 apartment 呼叫。 此選項適用於使用兩個執行緒模型的類別。  
  
 使用此選項時，類別必須確保執行緒安全的資料。 此外，彙總無限制執行緒封送處理器，且需要使用取自其他物件的介面指標的物件必須執行一些額外步驟以確保介面會正確地封送處理。 通常這牽涉到將介面指標儲存在全域介面表 (GIT)，以及每次使用時從 GIT 取得指標。 ATL 提供類別[CComGITPtr](../atl/reference/ccomgitptr-class.md)可協助您使用儲存在 GIT 中的介面指標。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [使用全域介面資料表的時機](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [同處理序執行緒問題](http://msdn.microsoft.com/library/windows/desktop/ms687205)

