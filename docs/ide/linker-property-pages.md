---
title: 連結器屬性頁 | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
dev_langs:
- C++
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cec232bb4e4f2f6ac1ab9af703b368eec0ba5dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331515"
---
# <a name="linker-property-pages"></a>連結器屬性頁

本主題會討論 [一般] 連結器屬性頁上的下列屬性。 如需此頁面的 Linux 版本，請參閱[連結器屬性 (Linux C++)](../linux/prop-pages/linker-linux.md)。

## <a name="general-page-properties"></a>一般頁面屬性

### <a name="ignore-import-library"></a>忽略匯入程式庫

這個屬性會告知連結器不要將這個組建所產生的任何 .lib 輸出連結到任何相依專案。 這可讓專案系統處理在建置時不會產生 .lib 檔的 .dll 檔。 如果專案相依於另一個會產生 DLL 的專案，則專案系統會自動連結該個子專案所產生的 .lib 檔。 產生 COM Dll 或資源專用 DLL 的專案可能不需要這點；這些 DLL 沒有任何有意義的匯出。 如果 DLL 沒有任何匯出，連結器便不會產生 .lib 檔。 如果磁碟上沒有任何匯出的 .lib 檔，專案系統會告知連結器連結此 (遺漏的) DLL，連結就會失敗。 請使用 [忽略匯入程式庫] 屬性來解決此問題。 當設定為 [是] 時，專案系統會忽略該 .lib 檔是否存在，並且會導致相依於此專案的任何專案都不要與不存在的 .lib 檔連結。

若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。

### <a name="register-output"></a>登錄輸出

對組建輸出執行 `regsvr32.exe /s $(TargetPath)`，這只有在 .dll 專案上才有效。 對於 .exe 專案，則會忽略這個屬性。 若要註冊 .exe 輸出，請在組態上設定建置後事件，以執行已註冊之 .exe 檔一律需要的自訂登錄。

若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。

### <a name="per-user-redirection"></a>個別使用者重新導向

Visual Studio 中的註冊傳統上都在 HKEY_CLASSES_ROOT (HKCR) 進行。 使用 Windows Vista 和更新版本的作業系統，若要存取 HKCR 您必須以提升權限模式執行 Visual Studio。 開發人員不一定想要在提升權限的模式中執行，但仍然必須使用註冊。 個別使用者重新導向，可讓您不需要以此模式執行即可註冊。

個別使用者重新導向會強制將 HKCR 的任何寫入重新導向至 HKEY\_CURRENT\_USER (HKCU)。 如果關閉每個使用者重新導向，它可能會在程式嘗試寫入 HKCR 時導致[專案建置錯誤 PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md)。

### <a name="link-library-dependencies"></a>連結程式庫相依性

指定是否要連結由相依專案所產生的 .lib 檔。 一般而言，您會想連結 .lib 檔，但這可能不適用於特定 DLL 的情況。

您也可以提供檔案名稱和相對路徑以指定 .obj 檔案，例如 "..\\..\MyLibProject\MyObjFile.obj"。 如果 .obj 檔案的原始程式碼 #includes 先行編譯標頭檔；例如 pch.h，pch.obj 檔案位於和 MyObjFile.obj 相同的資料夾，而且您也必須新增 pch.obj 作為其他相依性。

### <a name="use-library-dependency-inputs"></a>使用程式庫相依性輸入

在大型專案中，當相依專案產生 .lib 檔時，會停用累加連結。 如果有許多相依專案產生 .lib 檔，建置應用程式可能會花很長的時間。 當這個屬性設定為 [是]，專案系統會針對相依專案所產生的 .lib 連結 .obj 檔，進而啟用累加連結。

如需如何存取 [一般] 連結器屬性頁的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

## <a name="see-also"></a>另請參閱

[選項對話方塊、專案和方案、VC++ 專案設定](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)  
[屬性頁](../ide/property-pages-visual-cpp.md)  