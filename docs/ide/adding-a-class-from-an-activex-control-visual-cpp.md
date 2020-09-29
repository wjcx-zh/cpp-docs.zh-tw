---
title: 從 ActiveX 控制項新增類別
ms.date: 11/08/2018
f1_keywords:
- vc.codewiz.class.axcontrol
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
- ActiveX Control Wizard
- add class from ActiveX control wizard [C++]
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
ms.openlocfilehash: d63f73e17e47f2cabb8f1a55c71325ec7068a2c8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500372"
---
# <a name="add-a-class-from-an-activex-control"></a>從 ActiveX 控制項新增類別

使用此精靈從可用 ActiveX 控制項中的介面建立 MFC 類別。 您可以將 MFC 類別新增至 [MFC 應用程式](../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)。

> [!WARNING]
> 在 Visual Studio 2017 15.9 版中，Microsoft 已淘汰此程式碼精靈，而且我們將會在 Visual Studio 的未來版本中予以移除。 使用者很少用到這個精靈。 移除此精靈不會影響 ATL 和 MFC 的一般支援。 若要對此次淘汰分享您的意見反應，請填寫[此問卷](https://www.surveymonkey.com/r/QDWKKCN)。 我們重視您的意見反應。
<!-- Blank comment here to separate the warning and note. -->
> [!NOTE]
> 建立 MFC 專案時不需要啟用自動化，即可從 ActiveX 控制項新增類別。

ActiveX 控制項是以元件物件模型 (COM) 為基礎的可重複使用軟體元件，支援各種 OLE 功能。 您可加以自訂，以符合多項軟體需求。 您可以在一般 ActiveX 控制項容器或網際網路上的全球資訊網網頁中使用 ActiveX 控制項。

**若要從 ActiveX 控制項新增 MFC 類別：**

1. 在 [方案總管]**** 或[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下您要將 ActiveX 控制項類別新增至其中的專案名稱。

1. 從捷徑功能表選擇 [新增]****，然後選擇 [新增類別]****。

1. 在 [[新增類別]](./adding-a-class-visual-cpp.md#add-class-dialog-box) 對話方塊的 [範本]**** 窗格中，選擇 [來自 ActiveX 控制項的 MFC 類別]****，然後選擇 [開啟]****，以顯示 [[從 ActiveX 控制項新增類別精靈]](#add-class-from-activex-control-wizard)。

在精靈中，您可以在 ActiveX 控制項中新增多個介面。 您也可以在單一精靈工作階段中，從多個 ActiveX 控制項建立類別。

您可以從系統中註冊的 ActiveX 控制項新增類別，或者可以從位於型別程式庫檔案 (.tlb、.olb、.dll、.ocx 或 .exe) 的 ActiveX 控制項新增類別，而不先在系統中註冊它們。 如需註冊 ActiveX 控制項的詳細資訊，請參閱[註冊 OLE 控制項](../mfc/reference/registering-ole-controls.md)。

精靈會為您從選取的 ActiveX 控制項新增的每個介面，建立 MFC 類別，類別會衍生自 [CWnd](../mfc/reference/cwnd-class.md) 或 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)。

## <a name="in-this-section"></a>本節內容

- [從 ActiveX 控制項 wizard 加入類別](#add-class-from-activex-control-wizard)

## <a name="add-class-from-activex-control-wizard"></a>從 ActiveX 控制項新增類別精靈

使用此精靈從可用的 ActiveX 控制項新增 MFC 類別。 此精靈會為您從所選 ActiveX 控制項新增的每個介面建立類別。

- **新增類別來源**

  指定建立類別的來源型別程式庫位置。

  |選項|描述|
  |------------|-----------------|
  |**登錄**|型別程式庫會在系統中註冊。 已註冊的型別程式庫會列於 [可用的 ActiveX 控制項]**** 中。|
  |**檔案**|型別程式庫不一定會在系統中註冊，但會儲存於檔案中。 在 [位置]**** 中提供檔案位置。|

- **可用的 ActiveX 控制項**

  指定目前在系統中註冊的 ActiveX 控制項。 從此清單選取要在 [介面]**** 清單中顯示其介面的 ActiveX 控制項。 如需註冊 ActiveX 控制項的詳細資訊，請參閱 [MFC activex 控制項：散發 activex 控制項](../mfc/mfc-activex-controls-distributing-activex-controls.md) 。

  若您在 [新增類別來源]**** 下選取 [檔案]****，就無法變更此方塊。

- **位置**

  指定 ActiveX 控制項的位置。 若您在 [新增類別來源]**** 下選取 [檔案]****，就可以提供具有型別程式庫的檔案位置。 若要瀏覽檔案的位置，請選取省略符號按鈕。

  若您在 [新增類別來源]**** 下選取 [登錄]****，就無法變更此方塊。

- **介面**

  指定 ActiveX 控制項中的介面。 精靈會使用 [可用 ActiveX 控制項]**** 內目前選取項目中的介面，或使用 [位置]**** 中所指定型別程式庫檔案內的介面。

  |傳輸按鈕|描述|
  |---------------------|-----------------|
  |**>**|新增目前在 [介面]**** 清單中選取的介面。 如果未選取任何介面，則無法使用。|
  |**>>**|新增 ActiveX 控制項中的所有介面。 精靈會使用 [可用 ActiveX 控制項]**** 內目前選取項目中的介面，或使用 [位置]**** 中所指定型別程式庫檔案內的介面。|
  |**\<**|移除目前在 [產生的類別]**** 清單中選取的類別。 如果目前未在 [產生的類別]**** 清單中選取任何類別，則無法使用。|
  |**\<\<**|移除 [產生的類別]**** 清單中的所有類別。 如果 [產生的類別]**** 清單是空的，則無法使用。|

- **產生的類別**

  指定要從使用或按鈕新增之介面產生的類別名稱 **>** **>>** 。 您可以選取此方塊以選取類別，然後使用向上或向下鍵捲動清單。 當您選取 [完成]**** 後，即可檢視 [類別]**** 方塊中產生的各個類別名稱，以及 [.h 檔案]**** 方塊中產生的各個檔案名稱。 一次只能在此方塊中選取一個類別。

  您可以在此清單中選取類別，然後選取來移除它 **<** 。 不需在 [產生的類別]**** 方塊中選取類別，即可移除所有類別。 選取 **<<** 即可移除 [ **產生的類別** ] 方塊中的所有類別。

- **類別**

   指定在 [產生的類別]**** 方塊中所選類別的名稱 (當您選取 [完成]**** 時，精靈會新增此名稱)。 您可以在 [類別]**** 方塊中編輯名稱。

- **.h 檔案**

  設定新物件類別的標頭檔名稱。 根據預設，此名稱是以您在 [產生的類別]**** 中提供的名稱為基礎。 選取省略符號按鈕，以將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 若您選擇現有的檔案，在您於精靈中選取 [完成]**** 之後，精靈才會將它儲存至所選位置。

  精靈不會覆寫檔案。 若您選取現有檔案的名稱，然後選取 [完成]****，精靈就會提示您決定是否要將類別宣告附加至檔案內容。 選取 [是]**** 可附加檔案，選取 [否]**** 則可返回精靈，並指定另一個檔案名稱。

- **.cpp 檔案**

  設定新物件類別的實作檔名稱。 根據預設，此名稱是以您在 [產生的類別]**** 中提供的名稱為基礎。 選取省略符號按鈕，以將檔案名稱儲存至您選擇的位置。 在您於精靈中選取 [完成]**** 之後，才會將檔案儲存至所選位置。

  精靈不會覆寫檔案。 若您選取現有檔案的名稱，然後選取 [完成]****，精靈就會提示您決定是否要將類別實作附加至檔案內容。 選取 [是]**** 可附加檔案，選取 [否]**** 則可返回精靈，並指定另一個檔案名稱。
