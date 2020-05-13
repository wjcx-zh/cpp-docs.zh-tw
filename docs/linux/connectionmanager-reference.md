---
title: ConnectionManager 參考
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 1c6236cedba88714e9918dd2c096b5e78d2f08ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "77258029"
---
# <a name="connectionmanager-reference"></a>ConnectionManager 參考

::: moniker range="<=vs-2017"

ConnectManager.exe 在 Visual Studio 2019 版 16.5 及更高版本中提供。

::: moniker-end

::: moniker range="vs-2019"

ConnectManager.exe 是一個命令列實用程式,用於管理 Visual Studio 外部的遠端開發連接。 它對於預配新開發計算機等任務很有用。 或者,使用它設置 Visual Studio 進行持續整合。您可以在開發人員命令提示視窗中使用它。 有關開發人員指令提示的詳細資訊,請參閱[使用命令列中的 Microsoft C++工具集](../build/building-on-the-command-line.md)。

ConnectManager.exe 在 Visual Studio 2019 版 16.5 及更高版本中提供。 它是**Linux 開發**中的一部分,在可視化工作室安裝程式中C++工作負載。 當您在安裝程式中選擇**連接管理器**元件時,它也會自動安裝。 在 *%VCIDE 安裝中,其\\\\\\%Linux\\bin 連線管理員管理員.exe*.

ConnectManager.exe 的功能也可在視覺工作室中提供。 要在"IDE"中管理遠端開發連接,在功能表欄上,請選擇 **「工具** > **選項**」以打開「選項」對話方塊。 在選項「對話框中,選擇**跨平台** > **連線管理員**。

## <a name="syntax"></a>語法

> **連線管理員.exe***指令*\[*參數*\[=*選項*|

### <a name="commands-and-arguments"></a>指令與參數

- **新增***\@使用者 主機*\[ **--***連接埠*= \[ **--密碼***密碼*= \[ **--私密金鑰***privatekey_file*]

  驗證並添加新連接。 默認情況下,它使用埠 22 和密碼身份驗證。 (系統將提示您輸入密碼。使用 **--密碼**和 **-私密金鑰**為私密金鑰指定密碼。

- **remove**\[刪除*connection_id*\|connection_id*使用者\@* 主機\[ **--連接埠***port**

  刪除連接。 如果未指定參數,系統將提示您指定要刪除的連接。

- **全部刪除**

  刪除所有存儲的連接。

- list

  顯示所有存儲連接的資訊和指示。

- **說明**

  顯示幫助螢幕。

- **version**

  顯示版本資訊。

### <a name="options"></a>選項。

- **-q** **, - 安靜**

  防止輸出到`stdout``stderr`或 。

- **--無提示**

  在適當的時候失敗而不是提示。

- **--no-verify**

  添加或修改連接,無需身份驗證。

- **--檔案***名稱*

  從提供的*檔案名*讀取連接資訊。

- **--無遙測**

  禁用將使用方式數據發送回 Microsoft。 除非傳遞**了 --無遙測**標誌,否則將收集使用方式數據並將其發送回 Microsoft。  

- **-n** **, -- 幹運行**

  執行命令的幹運行。

- **-p**

  與 **-密碼**相同。

- **-i**

  與**私鑰**相同。

## <a name="examples"></a>範例

此命令為本地主機上名為"使用者"的使用者添加連接。 連線使用金鑰檔進行身份驗證,在*\.%USERPROFILE% ssh_id_rsa*中找到。

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

此命令從連接清單中刪除 ID 1975957870 的連接。

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>另請參閱

[連線至 Visual Studio 中的目標 Linux 系統](connect-to-your-remote-linux-computer.md)

::: moniker-end
