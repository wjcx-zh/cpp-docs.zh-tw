---
title: "QueryInterface |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: QueryInterface
dev_langs: C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5714eab684066e74a6d56144d915460b4312f4c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="queryinterface"></a>QueryInterface
雖然沒有的機制之物件可以用來表示它提供以靜態方式 （它具現化之前） 的功能，但基本的 COM 機制是使用**IUnknown**方法呼叫[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 每個介面衍生自**IUnknown**，因此每個介面的實作`QueryInterface`。 不論實作中，這個方法會查詢物件使用呼叫端想要指標之介面的 IID。 如果物件支援該介面，`QueryInterface`擷取介面的指標，同時也呼叫`AddRef`。 否則，它會傳回**E_NOINTERFACE**錯誤碼。  
  
 請注意，您必須遵守[參考計數](../atl/reference-counting.md)隨時都能的規則。 如果您呼叫**發行**上遞減參考計數為零的介面指標，您不應該使用該指標一次。 有時候您可能需要取得物件的弱式參考 （也就是您可能想要取得其中一個介面的指標，而不會遞增參考計數），但不是可接受的做法是藉由呼叫`QueryInterface`後面**發行**。 在這種方式取得的指標無效，且不應使用。 這更輕易地時，即可明顯[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)定義，所以定義這個巨集是有用的方式，尋找參考計數錯誤。  
  
## <a name="see-also"></a>請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [在物件中巡覽的 QueryInterface:](http://msdn.microsoft.com/library/windows/desktop/ms687230)

