---
title: "IUnknown |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IUnknown
dev_langs: C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e46ee55412c591558389bb7ac42116431eaaa6ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)的每個其他 COM 介面的基底介面。  這個介面會定義三種方法： [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)， [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)，和[發行](http://msdn.microsoft.com/library/windows/desktop/ms682317)。 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)允許介面使用者要求的物件之間的介面指標。 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)和[發行](http://msdn.microsoft.com/library/windows/desktop/ms682317)實作參考計數的介面上。  
  
## <a name="see-also"></a>請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [IUnknown 和介面繼承](http://msdn.microsoft.com/library/windows/desktop/ms692713)

