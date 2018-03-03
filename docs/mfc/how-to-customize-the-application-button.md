---
title: "如何： 自訂應用程式按鈕 |Microsoft 文件"
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
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a4a150985bd5c552b361620df87e34511ef8027
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-customize-the-application-button"></a>如何：自訂應用程式按鈕
當您按一下 [應用程式] 按鈕時，會顯示命令的功能表。 通常，功能表包含檔案的相關命令例如**開啟**，**儲存**，**列印**，和**結束**。  
  
 ![MFC 功能區應用程式按鈕](../mfc/media/application_button.png "application_button")  
  
 若要自訂的應用程式按鈕，開啟該**屬性**視窗中，修改其屬性，然後再預覽 功能區控制項。  
  
### <a name="to-open-the-application-button-in-the-properties-window"></a>在 [屬性] 視窗中開啟應用程式按鈕  
  
1.  在 Visual Studio 中，在**檢視**功能表上，按一下 **資源檢視**。  
  
2.  在**資源檢視**，按兩下功能區資源以顯示在設計介面上。  
  
3.  設計介面上，以滑鼠右鍵按一下 應用程式 按鈕功能表，然後按一下 **屬性**。  
  
## <a name="application-button-properties"></a>應用程式按鈕屬性  
 下表定義的應用程式按鈕的屬性。  
  
|屬性|定義|  
|--------------|----------------|  
|**按鈕**|包含應用程式功能表右下角出現的最多三個按鈕的集合。|  
|**標題**|指定控制項的文字。 不同於其他功能區項目中，應用程式按鈕所顯示的標題文字。 相反地，文字用於協助工具。|  
|**HDPI Image**|指定高 dpi (HDPI) 應用程式按鈕圖示的識別項。 在高 DPI 監視器中，執行應用程式時**HDPI Image**而非**映像**。|  
|**HDPI Large Images**|指定高 DPI 大型影像的識別項。 在高 DPI 監視器中，執行應用程式時**HDPI Large Images**而非**大型影像**。|  
|**HDPI Small Images**|指定高 DPI 小型影像的識別項。 在高 DPI 監視器中，執行應用程式時**HDPI Small Images**而非**Small Images**。|  
|**ID**|指定控制項的識別項。|  
|**影像**|指定應用程式按鈕圖示的識別項。 圖示是一個 32 位元 26 x 26 點陣圖的 alpha 透明。 按一下或停留應用程式按鈕時，會反白顯示的透明部分的圖示。|  
|**索引鍵**|指定啟用索引鍵提示巡覽時顯示的字串。 當您按下 alt 鍵，會啟用金鑰提示瀏覽。|  
|**大型影像**|指定包含一系列的 32x32 圖示影像的識別項。 圖示會使用主要項目集合中的按鈕。|  
|**主要項目**|包含在應用程式 功能表出現的功能表項目的集合。|  
|**MRU Caption**|指定最近使用清單面板上顯示的文字。|  
|**小型影像**|指定包含一系列的 16x16 圖示影像的識別項。 圖示會使用 「 按鈕 」 集合中的按鈕。|  
|**使用**|啟用或停用的最近使用清單的面板。 最近使用清單面板會顯示在應用程式 功能表上。|  
|**寬度**|指定單位為像素的 [最近使用清單] 面板的寬度。|  
  
 應用程式功能表未出現在設計介面。 若要檢視它，您必須預覽功能區，或執行應用程式。  
  
#### <a name="to-preview-the-ribbon-control"></a>預覽功能區控制項  
  
-   在**Ribbon 編輯器工具列**，按一下 **測試 Ribbon**。  
  
## <a name="see-also"></a>請參閱  
 [功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)

