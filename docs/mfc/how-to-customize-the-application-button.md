---
title: 如何：自訂應用程式按鈕
ms.date: 11/19/2018
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: ba29e9ad65e0bb1d2163e4051c7c7b53664d8817
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175323"
---
# <a name="how-to-customize-the-application-button"></a>如何：自訂應用程式按鈕

當您按一下 [應用程式] 按鈕時，會顯示命令的功能表。 通常，功能表會包含檔案相關命令這類**開放**，**儲存**，**列印**，以及**結束**。

![MFC 功能區應用程式按鈕](../mfc/media/application_button.png "MFC 功能區應用程式按鈕")

若要自訂的應用程式按鈕，開啟它**屬性**視窗中，修改其屬性，然後再預覽功能區控制項。

### <a name="to-open-the-application-button-in-the-properties-window"></a>若要開啟 [屬性] 視窗中的應用程式按鈕

1. 在 Visual Studio 中，在**檢視**功能表上，按一下**資源檢視**。

1. 在 **資源檢視**，連按兩下 功能區資源，以顯示設計介面上。

1. 設計介面上，以滑鼠右鍵按一下 [應用程式] 按鈕功能表，並再按**屬性**。

## <a name="application-button-properties"></a>應用程式按鈕屬性

下表定義的應用程式按鈕的內容。

|屬性|定義|
|--------------|----------------|
|**按鈕**|包含應用程式功能表右下角出現的最多三個按鈕的集合。|
|**標題**|指定控制項的文字。 與其他功能區項目中，不同的應用程式按鈕所顯示的標題文字。 相反地，文字用於存取範圍。|
|**HDPI Image**|指定高 dpi (HDPI) 應用程式按鈕圖示的識別項。 當應用程式在高 DPI 監視器中， **HDPI Image**而非**映像**。|
|**HDPI Large Images**|指定的高 DPI 的大型映像的識別碼。 當應用程式在高 DPI 監視器中， **HDPI Large Images**而非**Large Images**。|
|**HDPI Small Images**|指定的高 DPI 的小型映像的識別碼。 當應用程式在高 DPI 監視器中， **HDPI Small Images**而非**Small Images**。|
|**ID**|指定控制項的識別項。|
|**影像**|指定應用程式按鈕圖示的識別項。 圖示是 32 位元 26 x 26 點陣圖具有 alpha 透明度。 應用程式按鈕已按下或暫留時，會反白顯示之圖示的透明部分。|
|**索引鍵**|指定啟用按鍵提示巡覽時所顯示的字串。 當您按下 alt 鍵，已啟用按鍵提示瀏覽。|
|**大型映像**|指定包含一系列的 32x32 圖示的映像的識別碼。 圖示會使用主要項目集合中的按鈕。|
|**主要的項目**|包含應用程式功能表出現的功能表項目的集合。|
|**MRU 標題**|指定最近使用清單的面板上顯示的文字。|
|**小型影像**|指定包含一系列的 16x16 圖示的映像的識別碼。 圖示會使用 「 按鈕 」 集合中的按鈕。|
|**使用**|啟用或停用 [最近使用清單] 面板。 最近使用清單 面板會顯示在應用程式 功能表上。|
|**寬度**|指定像素為單位的最新的清單 面板的寬度。|

應用程式功能表不會出現在設計介面上。 若要檢視它，您必須預覽功能區，或執行應用程式。

#### <a name="to-preview-the-ribbon-control"></a>預覽功能區控制項

- 在  **Ribbon 編輯器工具列**，按一下**測試 Ribbon**。

## <a name="see-also"></a>另請參閱

[功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)
