---
title: 連結器屬性頁 |Microsoft 文件
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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-property-pages"></a>連結器屬性頁

本主題會討論下列屬性對**一般**連結器屬性頁。 此頁面的 Linux 版本，請參閱[連結器屬性 （Linux c + +）](../linux/prop-pages/linker-linux.md)。

## <a name="general-page-properties"></a>屬性 [一般] 頁面

### <a name="ignore-import-library"></a>忽略匯入程式庫

這個屬性會告知連結器未連結到任何相依專案的這個組建所產生的任何.lib 輸出。 這可讓專案系統來處理不會產生的.lib 檔建置時的.dll 檔案。 如果專案相依於另一個會產生 DLL 的專案，專案系統會自動連結的子專案所產生的.lib 檔案。 這可能不需要由 COM Dll 或資源專用 Dll; 要產生的專案這些 Dll 並沒有任何有意義的匯出。 如果 DLL 中不有任何匯出，連結器不會產生的.lib 檔案。 如果沒有匯出.lib 檔存在於磁碟上專案系統會告知連結器連結此 （遺漏） dll，連結就會失敗。 使用**忽略匯入程式庫**屬性若要解決此問題。 當設定為**是**，專案系統會忽略該.lib 檔案是否存在，並會導致相依於此專案不使用不存在的.lib 檔案連結至任何專案。

若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。

### <a name="register-output"></a>登錄輸出

執行`regsvr32.exe /s $(TargetPath)`組建輸出時，這是.dll 專案上才有效。 .Exe 專案，則會忽略這個屬性。 若要註冊.exe 輸出，請執行所需的已註冊的.exe 檔案的自訂登錄組態上設定建置後事件。

若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。

### <a name="per-user-redirection"></a>個別使用者重新導向

傳統上尚未註冊 Visual Studio 中的執行的 HKEY_CLASSES_ROOT (HKCR)。 使用 Windows Vista 和更新版本的作業系統，存取 HKCR 您必須執行 Visual Studio 中提高權限模式。 開發人員不一定想要在提升權限模式下執行，但仍然必須使用註冊。 個別使用者重新導向，可讓您註冊不需要在此模式中執行。

個別使用者重新導向會強制重新導向至 HKEY hkcr 的任何寫入\_目前\_使用者 (HKCU)。 如果每次使用者重新導向已關閉，它可能會導致[專案建置錯誤 PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md)程式嘗試寫入 HKCR。

### <a name="link-library-dependencies"></a>連結程式庫相依性

指定是否要連結的相依專案所產生的.lib 檔案。 一般而言，您要連結的.lib 檔案，但這可能不是特定 Dll 的情況。

您也可以指定.obj 檔案，藉由提供的檔名和相對路徑，例如 「...\\..\MyLibProject\MyObjFile.obj"。 如果.obj 檔案的原始程式碼 #includes 先行編譯標頭檔，例如 pch.h，pch.obj 檔案位於 MyObjFile.obj，相同的資料夾，而且您也必須加入 pch.obj 做為其他相依性。

### <a name="use-library-dependency-inputs"></a>使用程式庫相依性輸入

在大型專案中，當相依專案產生的.lib 檔時，累加連結已停用。 如果有許多相依專案產生的.lib 檔，請建置應用程式可能會花很長的時間。 當這個屬性設定為**是**，進而啟用累加連結的相依專案所產生的.lib 檔進行的.obj 檔中的專案系統連結。

如需有關如何存取資訊**一般**連結器屬性頁上，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

## <a name="see-also"></a>另請參閱

[選項對話方塊、專案和方案、VC++ 專案設定](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)  
[屬性頁](../ide/property-pages-visual-cpp.md)  