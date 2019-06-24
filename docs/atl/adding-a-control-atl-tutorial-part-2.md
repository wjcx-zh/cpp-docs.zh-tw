---
title: 加入控制項 (ATL 教學課程，第 2 部分)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: 53f38d63a44328bf014f04635a24989a875ddf1e
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344334"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>加入控制項 (ATL 教學課程，第 2 部分)

在此步驟中，您可以將控制項新增至您的專案，建置它，並在網頁上進行測試。

## <a name="procedures"></a>程序

### <a name="to-add-an-object-to-an-atl-project"></a>將物件新增至 ATL 專案

1. 在 [方案總管]  中，以滑鼠右鍵按一下 `Polygon` 專案。

1. 指向**新增**捷徑功能表，然後按一下 [**新項目**] 子功能表中。

    [新增項目]  對話方塊隨即出現。 在左側的樹狀結構中列出的不同物件分類。

1. 按一下  **ATL**資料夾。

1. 從右側的範本清單中，選取**ATL 控制項**。 按一下 [加入]  。 **ATL 控制項**精靈隨即開啟，而且您可以設定控制項。

1. 型別`PolyCtl`為簡短名稱，並注意其他欄位會自動完成。 不要按**完成**但因為您必須進行更多的變更。

**ATL 控制項**精靈**名稱**頁面包含下列欄位：

|欄位|內容|
|-----------|--------------|
|**簡短名稱**|您輸入控制項的名稱。|
|**類別**|C++建立來實作控制項的類別名稱。|
|**.h 檔案**|建立來包含定義的檔案C++類別。|
|**.cpp 檔**|若要包含的實作所建立的檔案C++類別。|
|**CoClass**|這個控制項元件類別的名稱。|
|**Interface**|它的自訂方法和屬性，控制將實作的介面名稱。|
|**Type**|控制項的描述。|
|**ProgID**|可以用來查詢控制項 CLSID 的可讀取的名稱。|

您可以找到數個額外的設定中必須變更**ATL 控制項**精靈。

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>若要啟用對豐富錯誤資訊和連接點

1. 按一下 **選項**來開啟**選項**頁面。

1. 選取 **連接點**核取方塊。 此選項會在 IDL 檔案中建立流出介面的支援。

您也可以加入介面以擴充控制項的功能。

### <a name="to-extend-the-controls-functionality"></a>若要擴充控制項的功能

1. 按一下 **介面**來開啟**介面**頁面。

1. 選取  `IProvideClassInfo2` ，按一下 **向上**箭號將其移至**支援**清單。

1. 選取  `ISpecifyPropertyPages` ，按一下 **向上**箭號將其移至**支援**清單。

您也可以讓控制項*可插入*，這表示它是內嵌到支援內嵌的物件，例如 Excel 或 Word 的應用程式。

### <a name="to-make-the-control-insertable"></a>表示將控制項設為可插入

1. 按一下 **外觀**來開啟**外觀**頁面。

1. 選取  **Insertable&apos**核取方塊。

顯示物件的多邊形必須純色填滿色彩，因此您必須新增`Fill Color`內建屬性。

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>若要加入的填滿色彩內建屬性，並建立控制項

1. 按一下 **內建屬性**來開啟**內建屬性**頁面。

1. 底下**不支援**，向下捲動可能的內建屬性的清單。 選取  `Fill Color` ，按一下 **向上**箭號將其移至**支援**清單。

1. 選擇 [完成]  。

精靈會建立控制項，數個程式碼變更和加入檔案，就會發生。 會建立下列檔案：

|檔案|描述|
|----------|-----------------|
|PolyCtl.h|包含大部分的實作的C++類別`CPolyCtl`。|
|PolyCtl.cpp|包含的其餘部分`CPolyCtl`。|
|PolyCtl.rgs|包含用來登錄此控制項登錄指令碼的文字檔。|
|PolyCtl.htm|Web 網頁，其中包含新建立之控制項的參考。|

精靈也會進行下列程式碼變更：

- 新增`#include`stdafx.h 和 stdafx.cpp 檔案要包含 ATL 的陳述式支援控制項所需的檔案。

- 變更 Polygon.idl 以加入新控制項的詳細資料。

- 將新的控制項加入至 Polygon.cpp 中的物件對應中。

您現在可以建置的控制項，若要查看作用中。

## <a name="building-and-testing-the-control"></a>建置和測試控制項

### <a name="to-build-and-test-the-control"></a>建置和測試控制項

1. 在 **建置**功能表上，按一下**建置多邊形**。

    一旦控制項完成建置，以滑鼠右鍵按一下中的 PolyCtl.htm**方案總管**，然後選取**瀏覽器中的檢視**。 包含控制項的 HTML 網頁會顯示。 您應該會看到標題"ATL 8.0 測試頁物件 PolyCtl 的 」，與您的控制項文字 PolyCtl 的頁面。

> [!NOTE]
> 如果看不到控制項，知道某些瀏覽器需要執行 ActiveX 控制項的設定調整。 請參閱有關如何啟用 ActiveX 控制項的瀏覽器的文件。

> [!NOTE]
> 當完成本教學課程中，如果您收到錯誤訊息，無法建立 DLL 檔案後，關閉 PolyCtl.htm 檔案和 ActiveX 控制項測試容器，並重新建置方案。 如果您仍然無法建立 DLL 時，會重新啟動電腦，或先登出，如果您使用終端機服務。

接下來，您會將自訂屬性加入控制項。

[回到步驟 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [繼續至步驟 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
