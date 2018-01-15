---
title: "ATL 控制項： 一般支援類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.controls
dev_langs: C++
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 542245186fea67a0945414de56ad31b3b975eae3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="controls-general-support-classes"></a>控制項： 一般支援類別
下列類別會提供一般支援，ATL 控制項：  
  
-   [CComControl](../atl/reference/ccomcontrol-class.md) ATL 的控制項不可或缺的 helper 函式和資料成員所組成。  
  
-   [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md)提供控制項所需的方法。  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md)提供控制，透過此容器進行通訊的主要方法。 管理啟用和停用就地控制項的作業。  
  
-   [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md)結合成單一的呼叫，以協助容器載入控制項時，避免產生延遲初始化。  
  
-   [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md)提供最少的滑鼠互動，否則為非作用中的控制項。  
  
## <a name="sample-program"></a>範例程式  
 [ATLFire](../visual-cpp-samples.md)  
  
## <a name="related-articles"></a>相關文章  
 [ATL 教學課程](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../atl/atl-class-overview.md)

