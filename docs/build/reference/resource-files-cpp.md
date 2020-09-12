---
title: '專案資源檔 (c + +) '
ms.date: 05/14/2019
helpviewer_keywords:
- resource files
- resources [C++]
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: d37c3602d8939db609fc8af42dd764655195b24b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041012"
---
# <a name="project-resource-files-c"></a>專案資源檔 (c + +) 

資源是提供資訊給使用者的介面項目。 點陣圖、圖示、工具列和資料指標都是資源。 部分資源可以執行動作，例如從功能表選取，或在對話方塊中輸入資料。

如需詳細資訊，請參閱[使用資源](../../windows/working-with-resource-files.md)。

|檔案名稱|目錄位置|方案總管位置|描述|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.rc|*Projname*|原始程式檔|專案的資源指令檔。 根據專案類型，以及針對專案選取的支援 (例如工具列、對話方塊或 HTML)，資源指令檔會包含下列項目：<br /><br />- 預設功能表定義。<br />- 快速鍵和字串資料表。<br />-預設的 [ **關於** ] 對話方塊。<br />- 其他對話方塊。<br />-圖示檔 (res \\ *Projname*.ico) 。<br />- 版本資訊。<br />- 點陣圖。<br />- 工具列。<br />- HTML 檔案。<br /><br /> 資源檔包含標準 MFC 資源的 Afxres.rc 檔案。|
|偵錯工具|*Projname*|標頭檔|資源標頭檔，其中包含專案所使用之資源的定義。|
|*Projname*.rc2|*Projname*\res|原始程式檔|指令檔，其中包含專案所使用的其他資源。 您可以在專案的 .rc 檔案下包含 .rc2 檔案。<br /><br /> .rc2 檔案可用於包含數個不同專案所使用的資源。 您不必為不同的專案多次建立相同的資源，您可以將它們放在 .rc2 檔案中，再將 .rc2 檔案包含在主要 .rc 檔案中。|
|*Projname*.def|*Projname*|原始程式檔|DLL 專案的模組定義檔。 若是控制項，它會提供控制項的名稱和描述，以及執行階段堆積的大小。|
|*Projname*.ico|*Projname*\res|資源檔|專案或控制項的圖示檔。 當應用程式最小化時，就會出現此圖示。 您也可以在應用程式的 [關於]**** 方塊中使用此圖示。 根據預設，MFC 會提供 MFC 圖示，而 ATL 會提供 ATL 圖示。|
|*Projname*Doc.ico|*Projname*\res|資源檔|MFC 專案的圖示檔，其中包含文件/檢視架構的支援。|
|Toolbar.bmp|*Projname*\res|資源檔|點陣圖檔，代表工具列或選擇區中的應用程式或控制項。 此點陣圖會包含在專案的資源檔中。 初始工具列和狀態列是在 **CMainFrame** 類別中建構。|
|ribbon.mfcribbon-ms|*Projname*\res|資源檔|資源檔，其中包含定義功能區按鈕、控制項和屬性的 XML 程式碼。 如需詳細資訊，請參閱 [Ribbon Designer (MFC)](../../mfc/ribbon-designer-mfc.md)。|

## <a name="see-also"></a>另請參閱

[為 Visual Studio C++ 專案建立的檔案類型](file-types-created-for-visual-cpp-projects.md)
