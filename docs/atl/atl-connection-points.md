---
title: ATL 連接點 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 179f4329d55261d71d3d122e6a2601ce7e805c0f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="atl-connection-points"></a>ATL 連接點
可連接物件是指支援輸出介面的物件。 輸出介面可讓物件與用戶端通訊。 針對每個輸出介面，可連接物件都會公開一個連接點。 每個輸出介面都是由稱為接收 (sink) 的物件上的用戶端所實作。  
  
 ![連接點](../atl/media/vc2zw31.gif "vc2zw31")  
  
 每個連接點支援[IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)介面。 可連接物件會公開其連接點，以用戶端透過[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)介面。  
  
## <a name="in-this-section"></a>本節內容  
 [ATL 連接點類別](../atl/atl-connection-point-classes.md)  
 簡短說明支援連接點的 ATL 類別。  
  
 [將連接點新增至物件](../atl/adding-connection-points-to-an-object.md)  
 概述用來將連接點加入物件的步驟。  
  
 [ATL 連接點範例](../atl/atl-connection-point-example.md)  
 提供宣告連接點的範例。  
  
## <a name="related-sections"></a>相關章節  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)

