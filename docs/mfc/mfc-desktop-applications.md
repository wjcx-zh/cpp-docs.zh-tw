---
title: MFC 桌面應用程式
ms.date: 11/04/2016
f1_keywords:
- MFC
- mfc
helpviewer_keywords:
- libraries, MFC
- class libraries, MFC
- MFC, about MFC
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
ms.openlocfilehash: 042412000ba59c8400c5a3a64edae5d60756116a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239008"
---
# <a name="mfc-desktop-applications"></a>MFC 桌面應用程式

Microsoft Foundation Class (MFC) 程式庫提供許多 Win32 與 COM 應用程式開發介面的物件導向包裝函式。 雖然這個程式庫可以用來建立非常簡單的桌面應用程式，但還是在您需要開發包含多個控制項的較複雜使用者介面時最有用。 您可以使用 MFC 來建立 Office 樣式使用者介面的應用程式。

《MFC 參考》涵蓋構成 MFC 程式庫的類別、全域函式、全域變數和巨集。

每個類別所附的個別階層架構圖表對尋找基底類別會很有用。 《MFC 參考》通常不說明繼承的成員函式或繼承的運算子。 如需這些函式的詳細資訊，請參閱階層架構圖表描繪的基底類別。

每個類別的文件都包含類別概觀、依分類列出的成員摘要，以及成員函式、多載運算子和資料成員的主題。

公用和受保護類別成員僅在其是以一般方式使用於應用程式或衍生類別時，才會有文件的相關記載。 如需類別成員的完整清單，請參閱類別標頭檔。

> [!IMPORTANT]
>  MFC 類別和其成員不能在 Windows 執行階段環境中執行的應用程式。
>
>  多位元組字元編碼的 (MBCS) MFC 程式庫 (DLL) 不再隨附於 Visual Studio，但是可以當做 Visual Studio 附加元件。 如需詳細資訊，請參閱 < [MFC MBCS DLL 附加元件](mfc-mbcs-dll-add-on.md)。

## <a name="in-this-section"></a>本節內容

[概念](mfc-concepts.md)<br/>
MFC 主題的概念性文章。

[階層架構圖表](hierarchy-chart.md)<br/>
以視覺化方式詳細列出類別庫中的類別關聯性。

[類別概觀](class-library-overview.md)<br/>
依據分類列出 MFC 程式庫中的類別。

[逐步解說](walkthroughs-mfc.md)<br/>
包含逐步解說各種與 MFC 程式庫功能相關聯之工作的文件。

[技術提示](mfc-technical-notes.md)<br/>
提供 MFC 開發小組所撰寫有關類別庫之特定主題的連結。

[MFC 自訂](customization-for-mfc.md)<br/>
提供一些自訂您的 MFC 應用程式的秘訣。

[類別](reference/mfc-classes.md)<br/>
提供 MFC 類別的標頭檔資訊和連結。

[內部類別](reference/internal-classes.md)<br/>
MFC 內部使用。 為求完整起見，本節會說明這些內部類別，但是它們並不適合直接在您的程式碼中使用。

[巨集和全域](reference/mfc-macros-and-globals.md)<br/>
提供 MFC 程式庫中巨集與全域函式的連結。

[結構、樣式、回呼和訊息對應](reference/structures-styles-callbacks-and-message-maps.md)<br/>
提供 MFC 程式庫所使用之結構、樣式、回呼及訊息對應的連結。

[MFC 精靈和對話方塊](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Visual Studio 中用於建立 MFC 應用程式之功能的指南。

[使用資源檔](../windows/working-with-resource-files.md)<br/>
如何使用資源檔來管理靜態使用者介面資料，例如 UI 字串和對話方塊版面配置。

## <a name="related-sections"></a>相關章節

[階層架構圖表分類](hierarchy-chart-categories.md)<br/>
依分類說明 MFC 階層架構圖表。

[ATL/MFC 共用類別](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
提供 MFC 和 ATL 之間共用的類別的連結。

[MFC 範例](../overview/visual-cpp-samples.md)<br/>
提供示範如何使用 MFC 之範例的連結。

[Visual C++ 程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
提供 Visual C++ 隨附之各種程式庫的連結，這些程式庫包括 ATL、MFC、OLE DB 樣板、C 執行階段程式庫和 C++ 標準程式庫。

[Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)<br/>
提供使用 Visual Studio 偵錯工具來更正應用程式或預存程序 (Stored Procedure) 中邏輯錯誤的連結。

## <a name="see-also"></a>另請參閱

[MFC 和 ATL](mfc-and-atl.md)
