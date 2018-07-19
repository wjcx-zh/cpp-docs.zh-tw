---
title: IUnknown |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d832d2978bf9db82b290d77b236fea1c9bcada58
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953038"
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)是所有其他 COM 介面的基底介面。  這個介面會定義三種方法： [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)， [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)，並[版本](http://msdn.microsoft.com/library/windows/desktop/ms682317)。 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)可讓介面使用者向物件的另一個介面的指標。 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)並[發行](http://msdn.microsoft.com/library/windows/desktop/ms682317)實作參考計數介面。  
  
## <a name="see-also"></a>另請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [IUnknown 和介面繼承](http://msdn.microsoft.com/library/windows/desktop/ms692713)

