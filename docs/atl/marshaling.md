---
title: 封送處理 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2b8b82d5369aa536dab638efa379089325d10b1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="marshaling"></a>封送處理
封送處理 COM 技術可讓一個處理序，以用於另一個處理序中物件所公開的介面。 封送處理 COM 提供程式碼 （或使用的介面實作項所提供的程式碼） 中，將方法的參數封裝成可移動的跨處理序 （以及跨網路在其他電腦上執行的處理序） 的格式和解壓縮這些參數另一端。 同樣地，COM 必須執行相同的步驟，在從呼叫傳回。  
  
> [!NOTE]
>  封送處理時，通常無法必要物件相同的程序中使用物件所提供的介面。 不過，封送處理可能需要在執行緒之間。  
  
## <a name="see-also"></a>另請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [封送處理的詳細資料](http://msdn.microsoft.com/library/windows/desktop/ms692621)

