---
title: "彙總 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8dbb0332bc7e55464e5b8af9d0b57e236f23dc86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="aggregation"></a>彙總
但有些的時候，當物件的實作項想要利用預先建置的另一個物件所提供的服務。 此外，還可能想要顯示的第一個自然一部分此第二個物件。 COM 完成這兩個目標透過內含項目和彙總。  
  
 彙總表示包含 （外部） 物件會建立包含 （內部） 的物件做為其建立程序的一部分，而且內部物件的介面會公開外部。 物件可讓本身或不是可彙總。 如果是，它必須遵循特定規則才能正常運作的彙總。  
  
 所有主要**IUnknown**所包含的物件呼叫方法必須委派給與包含物件。  
  
## <a name="see-also"></a>請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [重複使用的物件](http://msdn.microsoft.com/library/windows/desktop/ms678443)

