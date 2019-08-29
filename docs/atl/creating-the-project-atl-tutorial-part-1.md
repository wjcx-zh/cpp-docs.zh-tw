---
title: 建立專案 (ATL 教學課程，第 1 部分)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 5bb4c6edffd13e13a451b203feea9a03461a9318
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108376"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>建立專案 (ATL 教學課程，第 1 部分)

本教學課程會逐步引導您逐步執行非屬性化 ATL 專案, 以建立會顯示多邊形的 ActiveX 物件。 物件包含的選項可讓使用者變更組成多邊形的側邊數目, 以及用來重新整理顯示的程式碼。

> [!NOTE]
> 本教學課程會建立與多邊形範例相同的原始程式碼。 如果您想要避免手動輸入原始程式碼, 可以從[多邊形範例摘要](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon)下載。 接著, 您可以在進行教學課程時參考多邊形原始程式碼, 或使用它來檢查您自己專案中的錯誤。
> 若要編譯, 請開啟*pch* (Visual Studio 2017 和更早版本中的*stdafx.h* ), 並取代:
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
> 取代為
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
> 編譯器仍然會抱怨`regsvr32`未正確結束, 但您仍應建立控制項的 DLL, 並可供使用。

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>若要使用 ATL 專案 Wizard 建立初始 ATL 專案

1. 在 Visual Studio 2017 和更早版本中: **[檔案**] [**新增** > 專案]。  >  開啟 [**視覺效果C++**  ] 索引標籤, 然後選取 [ **MFC/ATL**]。 選取 [ **ATL 專案**]。

   在 Visual Studio 2019:  > 選擇 [檔案] [新增專案], 在 [搜尋] 方塊中輸入 "atl", 然後選擇 [atl 專案]。 > 

1. 輸入*多邊形*做為專案名稱。

    原始程式碼的位置通常會預設為 \Users\\ \<username > \source\repos, 並會自動建立新的資料夾。

1. 在 Visual Studio 2019 中, 接受預設值, 然後按一下 **[確定]** 。 
   在 Visual Studio 2017 中, 按一下 **[確定]** 以開啟 [ **ATL 專案**嚮導]。 按一下 [**應用程式設定**] 以查看可用的選項。 因為此專案會建立控制項, 且控制項必須是同進程伺服器, 所以請將**應用程式類型**保留為 DLL。 按一下 [確定]。

Visual Studio 會產生數個檔案來建立專案。 您可以藉由展開`Polygon`物件, 在**方案總管**中查看這些檔案。 檔案如下所示。

::: moniker range="<=vs-2017"

|檔案|描述|
|----------|-----------------|
|多邊形 .cpp|包含`DllMain`、 `DllCanUnloadNow`、 `DllGetClassObject` 、和`DllUnregisterServer`的執行。 `DllRegisterServer` 也包含物件對應, 也就是專案中的 ATL 物件清單。 這一開始是空白的。|
|多邊形 .def|此模組定義檔會提供連結器, 其中包含 DLL 所需之匯出的相關資訊。|
|多邊形 .idl|介面定義語言檔案, 描述物件特定的介面。|
|多邊形 .rgs|此登入指令檔包含註冊程式 DLL 的資訊。|
|多邊形 .rc|資源檔, 一開始包含版本資訊和包含專案名稱的字串。|
|偵錯工具|資源檔的標頭檔。|
|Polygonps .def|此模組定義檔會提供連結器, 其中包含 proxy 和 stub 程式碼所需之匯出的相關資訊, 以支援跨各單元的呼叫。|
|stdafx.cpp|將`#include` *stdafx.h*的檔案。|
|stdafx.h|將`#include`和先行編譯 ATL 標頭檔的檔案。|

::: moniker-end

::: moniker range=">=vs-2019"

|檔案|描述|
|----------|-----------------|
|多邊形 .cpp|包含`DllMain`、 `DllCanUnloadNow`、 `DllGetClassObject` 、和`DllUnregisterServer`的執行。 `DllRegisterServer` 也包含物件對應, 也就是專案中的 ATL 物件清單。 這一開始是空白的。|
|多邊形 .def|此模組定義檔會提供連結器, 其中包含 DLL 所需之匯出的相關資訊。|
|多邊形 .idl|介面定義語言檔案, 描述物件特定的介面。|
|多邊形 .rgs|此登入指令檔包含註冊程式 DLL 的資訊。|
|多邊形 .rc|資源檔, 一開始包含版本資訊和包含專案名稱的字串。|
|偵錯工具|資源檔的標頭檔。|
|Polygonps .def|此模組定義檔會提供連結器, 其中包含 proxy 和 stub 程式碼所需之匯出的相關資訊, 以支援跨各單元的呼叫。|
|pch .cpp|將會`#include`是*pch*的檔案。|
|pch. h|將`#include`和先行編譯 ATL 標頭檔的檔案。|

::: moniker-end

1. 在 [方案總管] 中，以滑鼠右鍵按一下 `Polygon` 專案。

1. 在快捷方式功能表上, 按一下 [**屬性**]。

1. 按一下 [**連結器**]。 將 [**每個 UserRedirection** ] 選項變更為 **[是]** 。

1. 按一下 [確定]。

在下一個步驟中, 您會將控制項新增至您的專案。

[至步驟2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
