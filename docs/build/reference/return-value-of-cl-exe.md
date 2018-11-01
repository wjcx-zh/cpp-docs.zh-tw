---
title: cl.exe 的傳回值
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 39b53731d94e3b5ff5fcb666caac6a584c34d287
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656075"
---
# <a name="return-value-of-clexe"></a>cl.exe 的傳回值

cl.exe 傳回零，代表成功 (沒有錯誤)，否則即傳回非零。

如果您是從指令碼、powershell、.cmd 或 .bat 檔案進行編譯，cl.exe 的傳回值會很實用。 建議您擷取編譯器的輸出，萬一發生錯誤或警告，就可加以解決。

cl.exe 有太多可能的錯誤結束代碼，無法全部列出。 您可以查閱錯誤碼在 winerror.h 或 ntstatus.h 檔案套件包含在 Windows 軟體開發套件，在 %programfiles (x86) %\Windows\\<em>版本</em>\Include\shared\ 目錄。 以十進位格式傳回的錯誤碼必須轉換成十六進位才能進行搜尋。 例如，錯誤碼 -1073741620 轉換為十六進位會是 0xC00000CC。 這個錯誤是在 ntstatus.h 中找到，對應的訊息為「遠端伺服器上找不到指定的共用名稱」(The specified share name cannot be found on the remote server)。 如需可下載的 Windows 錯誤碼，請參閱[ &#91;MS ERREF&#93;: Windows 錯誤碼](https://msdn.microsoft.com/library/cc231196)。

您也可以使用 Visual Studio 中的錯誤查詢公用程式，找出編譯器錯誤訊息代表的意義。 在 Visual Studio 命令殼層中，輸入**errlook.exe**來啟動公用程式，或在 Visual Studio IDE 中，功能表列上，選擇**工具**，**錯誤查詢**。 輸入錯誤值，就可以找到與錯誤相關聯的描述文字。 如需詳細資訊，請參閱[ERRLOOK 參考](../../build/reference/errlook-reference.md)。

## <a name="remarks"></a>備註

以下範例 .bat 檔是使用 cl.exe 的傳回值。

```cmd
echo off
cl /W4 t.cpp
@if ERRORLEVEL == 0 (
   goto good
)

@if ERRORLEVEL != 0 (
   goto bad
)

:good
   echo "clean compile"
   echo %ERRORLEVEL%
   goto end

:bad
   echo "error or warning"
   echo %ERRORLEVEL%
   goto end

:end
```

## <a name="see-also"></a>另請參閱

[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)