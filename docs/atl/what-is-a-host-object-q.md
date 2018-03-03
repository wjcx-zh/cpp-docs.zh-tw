---
title: "何謂主機物件 (ATL) |Microsoft 文件"
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
- host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da735caa84c133b9cdf63fae5df8bdd3d5f774b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-a-host-object"></a>何謂主機物件
主物件是 COM 物件，表示 ATL 提供特定視窗的 ActiveX 控制項容器。 主應用程式物件的子類別容器視窗中，因此它可以反映至控制項的訊息，其提供必要的容器介面，以供控制項，且它會公開[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)和[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)介面，可讓您設定控制項的環境。  
  
 您可以使用主物件來設定容器的環境屬性。  
  
## <a name="see-also"></a>請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)

