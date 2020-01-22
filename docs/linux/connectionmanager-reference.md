---
title: ConnectionManager 參考
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 2b01bfbcd81984e7ddf32cd5ab0485fff17b3d2b
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520897"
---
# <a name="connectionmanager-reference"></a>ConnectionManager 參考

::: moniker range="<=vs-2017"

Visual Studio 2019 16.5 版和更新版本中提供了 ConnectionManager .exe。

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager 是一個命令列公用程式，可管理 Visual Studio 外部的遠端開發連接。 這適用于布建新開發電腦的工作。 或者，用它來設定持續整合的 Visual Studio。 您可以在開發人員命令提示字元視窗中使用它。 如需開發人員命令提示字元的詳細資訊，請參閱[從命令C++行使用 Microsoft 工具](..\build\building-on-the-command-line.md)組。

Visual Studio 2019 16.5 版和更新版本中提供了 ConnectionManager .exe。 這是在 Visual Studio 安裝程式中**使用C++** 工作負載進行 Linux 開發的一部分。 當您在安裝程式中選擇**連接管理員**元件時，也會自動安裝它。 它會安裝在 *% VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager*。

Visual Studio 也提供 ConnectionManager 的功能。 若要在 IDE 中管理遠端開發連接，請在功能表列上選擇 [**工具**] [ > **選項**] 以開啟 [選項] 對話方塊。 在 [選項] 對話方塊中，選取 [**跨平臺** > **連線管理員**]。

## <a name="syntax"></a>語法

> **ConnectionManager .exe** *命令*\[*引數*] \[*選項*]

### <a name="commands-and-arguments"></a>命令和引數

- **新增***使用者\@主機*\[ **--通訊埠** *]* \[ **--密碼***密碼*] \[ **--privatekey** *privatekey_file*]

  驗證並加入新的連接。 根據預設，它會使用埠22和密碼驗證。 （系統會提示您輸入密碼。）同時使用 **--password**和 **--privatekey**來指定私密金鑰的密碼。

- **移除**\[*connection_id* \|*使用者\@主機*\[ **--埠***埠*]]

  移除連接。 如果未指定任何引數，系統會提示您指定要移除的連接。

- **全部移除**

  移除所有儲存的連接。

- **list**

  顯示所有預存連接的資訊和識別碼。

- **help**

  顯示 [說明] 畫面。

- **version**

  顯示版本資訊。

### <a name="options"></a>選項

- **-q**、 **--quiet**

  防止輸出 `stdout` 或 `stderr`。

- **--no-提示**

  當適用時，會失敗而不是提示。

- **--no-驗證**

  新增或修改未驗證的連接。

- **--file** *filename*

  從提供的*檔案名*讀取連接資訊。

- **--無-遙測**

  停用將使用量資料傳送回 Microsoft。 除非傳遞 **--no 遙測**旗標，否則會收集使用量資料，並將其傳送回給 Microsoft。  

- **-n**， **--試執行**

  執行命令的試執行。

- **-p**

  與 **--password**相同。

- **-i**

  與 **--privatekey**相同。

## <a name="examples"></a>範例

此命令會為 localhost 上名為 "user" 的使用者新增連接。 連接會使用金鑰檔進行驗證，在 *% USERPROFILE%\.ssh \ id_rsa*中找到。

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

此命令會從連線清單中移除識別碼為1975957870的連接。

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>請參閱

[連接到您在 Visual Studio 中的目標 Linux 系統](connect-to-your-remote-linux-computer.md)

::: moniker-end
