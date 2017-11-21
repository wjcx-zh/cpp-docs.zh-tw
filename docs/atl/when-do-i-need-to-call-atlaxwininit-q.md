---
title: "何時需要呼叫 AtlAxWinInit？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinInit
dev_langs: C++
helpviewer_keywords: AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2ec7d8d15b8219071b593368ed539d92ff3c9032
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>何時需要呼叫 AtlAxWinInit？

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)註冊**"AtlAxWin80"**視窗類別 （以及幾個自訂視窗訊息），因此必須呼叫此函式，再重新建立主視窗。 不過，您不一定需要明確地呼叫此函式，因為主控應用程式開發介面 （和使用它們的類別） 通常會為您呼叫此函式。 沒有會呼叫此函式一次以上。 。  
  
## <a name="see-also"></a>另請參閱  
 何時需要呼叫 AtlAxWinTerm     
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)
