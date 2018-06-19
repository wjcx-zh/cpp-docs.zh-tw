---
title: 何謂主機物件 (ATL) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d197f02949f6eaaeee50b428338684135d1db27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357730"
---
# <a name="what-is-a-host-object"></a>何謂主機物件
主物件是 COM 物件，表示 ATL 提供特定視窗的 ActiveX 控制項容器。 主應用程式物件的子類別容器視窗中，因此它可以反映至控制項的訊息，其提供必要的容器介面，以供控制項，且它會公開[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)和[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)介面，可讓您設定控制項的環境。  
  
 您可以使用主物件來設定容器的環境屬性。  
  
## <a name="see-also"></a>另請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)

