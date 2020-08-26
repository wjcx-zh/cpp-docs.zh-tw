---
title: cl.exe 的傳回值
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 06e0993f6a96117ab73f22e73857843dfcc334a1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836721"
---
# <a name="return-value-of-clexe"></a>cl.exe 的傳回值

cl.exe 傳回零，代表成功 (沒有錯誤)，否則即傳回非零。

如果您是從指令碼、powershell、.cmd 或 .bat 檔案進行編譯，cl.exe 的傳回值會很實用。 建議您擷取編譯器的輸出，萬一發生錯誤或警告，就可加以解決。

cl.exe 有太多可能的錯誤結束代碼，無法全部列出。 您可以在% ProgramFiles (x86) % \ Windows 套件 \\ <em>版本</em>\Include\shared\ 目錄的 Windows 軟體開發套件中，查詢包含在 winerror.h 中的錯誤碼。 以十進位格式傳回的錯誤碼必須轉換成十六進位才能進行搜尋。 例如，錯誤碼 -1073741620 轉換為十六進位會是 0xC00000CC。 這個錯誤是在 ntstatus.h 中找到，對應的訊息為「遠端伺服器上找不到指定的共用名稱」(The specified share name cannot be found on the remote server)。 如需 Windows 錯誤代碼的可下載清單，請參閱 [&#91;ERREF&#93;： Windows 錯誤碼](/openspecs/windows_protocols/MS-ERREF)。

您也可以使用 Visual Studio 中的錯誤查詢公用程式，找出編譯器錯誤訊息代表的意義。 在 Visual Studio 命令 shell 中，輸入 **errlook.exe** 以啟動公用程式;或者，在 Visual Studio IDE 的功能表列上，選擇 [ **工具**]、[ **錯誤查閱**]。 輸入錯誤值，就可以找到與錯誤相關聯的描述文字。 如需詳細資訊，請參閱 [ERRLOOK 參考](errlook-reference.md)。

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

[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
