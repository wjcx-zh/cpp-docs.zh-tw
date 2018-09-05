---
title: 建立專案 (ATL 教學課程，第 1 部分) |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54b45ff8c7af8c8aaf7232cefa2bb4f002fc37be
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755614"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>建立專案 (ATL 教學課程，第 1 部分)

本教學課程將逐步引導您逐步完成建立 ActiveX 物件顯示多邊形的非屬性化 ATL 專案。 物件包含的選項可讓使用者變更重新整理顯示組成的 polygon 和程式碼的邊數。

> [!NOTE]
>  ATL 和 MFC 不正式支援 Visual Studio 的 Express 版本中。

> [!NOTE]
>  本教學課程會建立相同的原始程式碼，多邊形的範例。 如果您想要避免以手動方式輸入的原始程式碼，您可以下載從[Polygon 範例摘要](../visual-cpp-samples.md)。 當您逐步進行教學課程中，或使用它來查看您自己的專案中的錯誤，您接著可以參考多邊形的原始程式碼。

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>若要建立初始的 ATL 專案使用 ATL 專案精靈

1. 在 Visual Studio 開發環境中，按一下**的新**上**檔案**功能表，然後再按一下**專案**。

2. 按一下  **Visual c + + 專案**資料夾，然後選取**ATL 專案**。

3. 型別*多邊形*做為專案名稱。

     原始碼的位置通常會預設為 My Documents\Visual Studio 專案，並會自動建立新的資料夾。

4. 按一下 [**確定**和 ATL 專案精靈] 隨即開啟。

5. 按一下 **應用程式設定**若要查看可用的選項。

6. 如您所建立控制項，控制項必須是同處理序伺服器，讓**應用程式類型**做為 DLL。

7. 其他選項保留其預設值，然後按**完成**。

[ATL 專案精靈] 會產生數個檔案來建立專案。 您可以展開多邊形物件，在 [方案總管] 中檢視這些檔案。 以下列出的檔案。

|檔案|描述|
|----------|-----------------|
|Polygon.cpp|包含實作`DllMain`， `DllCanUnloadNow`， `DllGetClassObject`， `DllRegisterServer`，和`DllUnregisterServer`。 也包含物件的對應，也就是您的專案中的 ATL 物件的清單。 這是一開始空白的。|
|Polygon.def|此模組定義檔會提供您的 DLL 所需之匯出的相關資訊的連結器。|
|Polygon.idl|介面定義語言檔案，其中描述您物件的特定介面。|
|Polygon.rgs|此登錄指令碼包含註冊您的程式 DLL 的資訊。|
|Polygon.rc|資源檔，一開始包含版本資訊，以及包含專案名稱的字串。|
|偵錯工具|資源檔的標頭檔。|
|Polygonps.def|此模組定義檔會提供連結器支援在 apartment 之間的呼叫匯出所需的 proxy 和虛設常式程式碼的相關資訊。|
|stdafx.cpp|將檔案`#include`ATL 實作檔案。|
|stdafx.h|將檔案`#include`ATL 標頭檔。|

1. 在 [方案總管] 中，以滑鼠右鍵按一下`Polygon`專案。

2. 在捷徑功能表，按一下 **屬性**。

3. 按一下 **連結器**。 變更**每個 UserRedirection**選項設定為**是**。

4. 按一下 [確定 **Deploying Office Solutions**]。

在下一個步驟中，您會將控制項加入您的專案。

[至步驟 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
