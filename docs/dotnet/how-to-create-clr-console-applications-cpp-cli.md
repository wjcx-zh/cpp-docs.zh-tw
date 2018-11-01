---
title: 如何：建立 CLR 主控台應用程式 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
ms.openlocfilehash: fa45578b1e773e954fe692bd1c49e311626c35de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525640"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>如何：建立 CLR 主控台應用程式 (C++/CLI)

您可以使用主控台應用程式範本，建立已經有基本專案參考及檔案的主控台應用程式專案。

通常，主控台應用程式會編譯成獨立的可執行檔，但並不具圖形使用者介面。 使用者在命令提示字元執行主控台應用程式，並使用命令提示字元發出指令到執行中的應用程式。 應用程式也在命令提示字元提供輸出資訊。 主控台應用程式的即時性是學習程式設計技術的絕佳方式，而不需有實作使用者介面的考量。

當您使用主控台應用程式範本建立專案時，會自動加入這些參考和檔案：

- 這些 .NET Framework 命名空間的參考：

   - [System](https://msdn.microsoft.com/library/system.appdomainmanager.appdomainmanager.aspx)—這個命名空間包含了基本類別和基底類別，而這些類別會定義最常使用的值和參考資料類型、事件和事件處理常式、介面、屬性以及處理例外狀況。

   - mscorlib—支援 .NET Framework 開發的組件 DLL。

- 原始程式檔：

   - 主控台 (.cpp 檔) —您新建應用程式的主要原始程式檔和進入點。 它識別專案 .dll 檔案及專案命名空間。 在這個檔案中提供您自己的程式碼。

   - AssemblyInfo.cpp—包含您可用來修改專案組件中繼資料的資訊，其中包括屬性、檔案、資源、類型、版本資訊、簽章資訊等。 如需詳細資訊，請參閱 <<c0> [ 組件內容](/dotnet/framework/app-domains/assembly-contents)。

   - Stdafx.cpp—用於建置名稱為 Win32.pch 的先行編譯標頭檔及名稱為 StdAfx.obj 的先行編譯類型檔。

- 標頭檔：

   - Stdafx.h—用於建置名稱為 Win32.pch 的先行編譯標頭檔及名稱為 StdAfx.obj 的先行編譯類型檔。

   - resource.h—產生的 app.rc 的 Include 檔。

- 資源檔：

   - app.rc—程式的資源指令碼檔。

   - app.ico—程式的圖示檔。

- ReadMe.txt—描述專案中的檔案。

## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>建立通用語言執行平台 (CLR) 主控台應用程式專案

1. 在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。

1. 在 [新增專案]  對話方塊中，於 [已安裝的範本] 之下，選取 [Visual C++]  節點，選取 [CLR]  節點，然後選取主控台應用程式範本。

1. 在 [名稱]  方塊中輸入應用程式的唯一名稱。

   您可以指定其他專案和方案設定，不過，這些屬性並非必要。

1. 選擇 [確定]  按鈕。

## <a name="see-also"></a>另請參閱

[CLR 專案](../ide/files-created-for-clr-projects.md)

