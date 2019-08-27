---
title: 加入控制項 (ATL 教學課程，第 2 部分)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: b7952f42b24c4211a2c44ea71fd17e4f65c3421a
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630703"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>加入控制項 (ATL 教學課程，第 2 部分)

在此步驟中, 您會將控制項新增至您的專案、建立它, 然後在網頁上進行測試。

## <a name="procedures"></a>程序

### <a name="to-add-an-object-to-an-atl-project"></a>將物件新增至 ATL 專案

1. 在 [方案總管] 中，以滑鼠右鍵按一下 `Polygon` 專案。

1. 指向快捷方式功能表上的 [**加入**], 然後按一下子功能表中的 [**新增專案**]。

    [新增項目] 對話方塊隨即出現。 不同的物件分類會列在左側的樹狀結構中。

1. 按一下 [ **ATL** ] 資料夾。

1. 從右邊的範本清單中, 選取 [ **ATL 控制項**]。 按一下 [新增]。 [ **ATL 控制項**嚮導] 隨即開啟, 而且您可以設定控制項。

1. 輸入`PolyCtl`做為簡短名稱, 並請注意, 其他欄位會自動完成。 請不要按一下 **[完成]** , 因為您必須進行一些變更。

**ATL 控制項**wizard 的 [**名稱**] 頁面包含下欄欄位:

|欄位|內容|
|-----------|--------------|
|**簡短名稱**|您為控制項輸入的名稱。|
|**類別**|建立C++用來執行控制項的類別名稱。|
|**.h 檔案**|為了包含C++類別定義而建立的檔案。|
|**.cpp 檔**|為了包含C++類別的執行而建立的檔案。|
|**CoClass**|這個控制項的元件類別名稱。|
|**Interface**|控制項將在其上執行其自訂方法和屬性之介面的名稱。|
|**型別**|控制項的描述。|
|**ProgID**|可以用來查閱控制項 CLSID 的可讀取名稱。|

您會發現在**ATL 控制項**嚮導中必須變更幾個額外的設定。

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>若要啟用豐富錯誤資訊和連接點的支援

1. 按一下 [**選項**] 以開啟 [**選項**] 頁面。

1. 選取 [**連接點**] 核取方塊。 此選項會在 IDL 檔案中建立傳出介面的支援。

您也可以新增介面來擴充控制項的功能。

### <a name="to-extend-the-controls-functionality"></a>擴充控制項的功能

1. 按一下 [**介面**] 以開啟 [**介面**] 頁面。

1. 選取`IProvideClassInfo2`並按一下**向上**箭號, 將它移至**支援**的清單。

1. 選取`ISpecifyPropertyPages`並按一下**向上**箭號, 將它移至**支援**的清單。

您也可以將控制項*插入*, 這表示它可內嵌在支援內嵌物件 (例如 Excel 或 Word) 的應用程式中。

### <a name="to-make-the-control-insertable"></a>使控制項變成可插入

1. 按一下 [**外觀**] 以開啟 [**外觀**] 頁面。

1. 選取 [**插入**] 核取方塊。

物件所顯示的多邊形將具有純色填滿色彩, 因此您必須加入`Fill Color`內建屬性。

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>若要加入填滿色彩內建屬性並建立控制項

1. 按一下 [內建**屬性**] 以開啟 [**庫存屬性**] 頁面。

1. 在 [**不支援**] 下, 向下流覽可能的內建屬性清單。 選取`Fill Color`並按一下**向上**箭號, 將它移至**支援**的清單。

1. 選擇 [完成]。

當 wizard 建立控制項時, 會進行數個程式碼變更和新增檔案。 系統會建立下列檔案:

|檔案|描述|
|----------|-----------------|
|PolyCtl.h|包含C++類別`CPolyCtl`的大部分實作為。|
|PolyCtl.cpp|包含的其餘部分`CPolyCtl`。|
|PolyCtl.rgs|文字檔, 其中包含用來註冊控制項的登入指令檔。|
|PolyCtl.htm|網頁, 其中包含新建立之控制項的參考。|

此 wizard 也會變更下列程式碼:

- `#include`將語句加入至先行編譯標頭檔, 以包含支援控制項所需的 ATL 檔案。

- 變更多邊形 .idl 以包含新控制項的詳細資料。

- 將新的控制項加入至多邊形 .cpp 中的物件對應。

現在您可以建立控制項, 以查看其運作方式。

## <a name="building-and-testing-the-control"></a>建置和測試控制項

### <a name="to-build-and-test-the-control"></a>建置和測試控制項

1. 在 [**建立**] 功能表上, 按一下 [**建立多邊形**]。

    控制項完成建立後, 以滑鼠右鍵按一下**方案總管**中的 [PolyCtl], 然後選取 [**在瀏覽器中查看**]。 隨即顯示包含控制項的 HTML 網頁。 您應該會看到標題為「物件 PolyCtl 的 ATL 8.0 測試頁面」的頁面, 以及您的控制項, 即 PolyCtl 文字。

> [!NOTE]
> 如果看不到控制項, 請知道有些瀏覽器需要調整設定以執行 ActiveX 控制項。 如需如何啟用 ActiveX 控制項的相關資訊, 請參閱瀏覽器的檔。

> [!NOTE]
> 完成本教學課程時, 如果您收到無法建立 DLL 檔案的錯誤訊息, 請關閉 PolyCtl 檔案和 ActiveX 控制項測試容器, 然後重新建立解決方案。 如果您仍然無法建立 DLL, 請重新開機電腦, 或在使用終端機服務時登出。

接下來, 您會將自訂屬性加入至控制項。

[回到步驟 1](../atl/creating-the-project-atl-tutorial-part-1.md)&#124; [于步驟 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
