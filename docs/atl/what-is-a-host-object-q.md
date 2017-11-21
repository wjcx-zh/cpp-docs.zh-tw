---
title: "何謂主機物件 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ab37e9a9d3a19f250f52d5f5c60de41968012625
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="what-is-a-host-object"></a>何謂主機物件
主物件是 COM 物件，表示 ATL 提供特定視窗的 ActiveX 控制項容器。 主應用程式物件的子類別容器視窗中，因此它可以反映至控制項的訊息，其提供必要的容器介面，以供控制項，且它會公開[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)和[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)介面，可讓您設定控制項的環境。  
  
 您可以使用主物件來設定容器的環境屬性。  
  
## <a name="see-also"></a>另請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)

