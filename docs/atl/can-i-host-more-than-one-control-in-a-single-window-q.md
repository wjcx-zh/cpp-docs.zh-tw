---
title: 可以裝載多個控制項中的單一視窗嗎？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ceb9444b6371e261115bbf52ef5a249100772d1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356420"
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>可以裝載多個控制項中的單一視窗嗎？
您不可以裝載多個控制項中單一 ATL 主控視窗。 每個主機視窗被設計來保存 （這允許簡易的機制，可以處理訊息反映和控制每個環境的屬性） 一次只有一個控制項。 不過，若要讓使用者看到多個控制項的單一視窗中，它是建立多個主控件 windows 做為該視窗的子系的簡單方式。  
  
## <a name="see-also"></a>另請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)

