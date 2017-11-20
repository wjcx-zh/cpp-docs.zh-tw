---
title: "Rich Edit 控制項中的列印 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d93611d66d394d4ed182261d3bba3121464931d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="printing-in-rich-edit-controls"></a>Rich Edit 控制項中的列印
您所見的 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 來呈現指定的裝置，例如印表機其輸出。 您也可以指定的 rich edit 控制項的輸出裝置格式化的文字。  
  
 若要格式化的特定裝置的 rich edit 控制項內容的一部分，您可以使用[FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange)成員函式。 [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911)搭配此函式的結構指定的目標裝置的裝置內容 (DC) 以及格式化的文字範圍。  
  
 完成格式化後的文字輸出裝置，您可以將輸出傳送給裝置使用[DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband)成員函式。 重複使用`FormatRange`和`DisplayBand`，列印的 rich edit 控制項內容的應用程式可以實作矩形。 （帶狀是輸出的分成較小部分用於列印）。  
  
 您可以使用[SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice)來指定目標裝置的 rich edit 控制項的成員函式將其文字格式化。 此函式可用於所見即所得 （所見即所得） 格式，在其中應用程式將使用預設印表機字型度量資訊，而不螢幕的文字。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)

