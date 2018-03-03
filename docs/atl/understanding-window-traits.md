---
title: "ATL 視窗特性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fda95e4517d2717a89310a8e49a0c5b337feebcf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-window-traits"></a>了解視窗特性
視窗特性類別提供標準化的樣式，用於建立 ATL 視窗物件的簡單方法。 做為範本參數所接受視窗特性[CWindowImpl](../atl/reference/cwindowimpl-class.md)與其他 ATL 視窗類別，做為提供預設視窗樣式類別層級的方式。  
  
 如果視窗執行個體的建立者未提供明確的呼叫中的樣式[建立](../atl/reference/cwindowimpl-class.md#create)，您可以使用 traits 類別，以確保使用正確的樣式，還是建立視窗。 您甚至可以確保的某些樣式設該視窗類別的所有執行個體同時允許其他樣式設定針對每個執行個體。  
  
## <a name="atl-window-traits-templates"></a>ATL 視窗特性樣板  
 ATL 提供兩個視窗特性範本可讓您設定在編譯時期使用其樣板參數的預設樣式。  
  
|類別|描述|  
|-----------|-----------------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|使用此範本，當您想要提供預設的呼叫中不指定任何其他樣式時，才會使用的視窗樣式**建立**。 提供在執行的階段優先順序，透過在設定的樣式的樣式會編譯時間。|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|當您想要指定永遠必須設定的視窗類別的樣式，請使用這個類別。 在執行階段提供的樣式會與樣式設定在編譯時期使用位元 OR 運算子結合。|  
  
 除了這些範本，ATL 提供許多預先定義的特製化`CWinTraits`範本的視窗樣式常用的組合。 請參閱[CWinTraits](../atl/reference/cwintraits-class.md)參考文件的完整詳細資料。  
  
## <a name="custom-window-traits"></a>自訂視窗特性  
 在罕見的情況下提供 ATL 的樣板的特製化其中一種不敷使用和您需要建立自己的 traits 類別，您只需要建立會實作兩個靜態函式的類別：`GetWndStyle`和**GetWndStyleEx**:  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]  
  
 所有這些函式會在執行階段，它可用來產生新的樣式值傳遞給某個樣式值。 如果您的視窗 traits 類別當作 ATL 視窗類別的樣板引數，傳遞給這些靜態函式的樣式值將會做為樣式引數傳遞[建立](../atl/reference/cwindowimpl-class.md#create)。  
  
## <a name="see-also"></a>請參閱  
 [視窗類別](../atl/atl-window-classes.md)

