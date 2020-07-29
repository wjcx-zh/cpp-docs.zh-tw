---
title: /ENTRY (進入點符號)
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: 80833980b64e8fdd2a2f57b2dc40eb21c784b6f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232699"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (進入點符號)

```
/ENTRY:function
```

## <a name="arguments"></a>引數

*函數*<br/>
函數，指定 .exe 檔案或 DLL 的使用者定義起始位址。

## <a name="remarks"></a>備註

/ENTRY 選項會將進入點函式指定為 .exe 檔或 DLL 的起始位址。

必須將函式定義為使用 **`__stdcall`** 呼叫慣例。 參數和傳回值取決於程式是主控台應用程式、windows 應用程式或 DLL。 建議您讓連結器設定進入點，以便正確初始化 C 執行時間程式庫，並執行靜態物件的 c + + 函式。

根據預設，起始位址是 C 執行時間程式庫中的函式名稱。 連結器會根據程式的屬性來選取它，如下表所示。

|函式名稱|預設值|
|-------------------|-----------------|
|**mainCRTStartup** （或**wmainCRTStartup**）|使用/SUBSYSTEM： CONSOLE 的應用程式;呼叫 `main` （或 `wmain` ）|
|**WinMainCRTStartup** （或**wWinMainCRTStartup**）|使用/SUBSYSTEM：**WINDOWS**的應用程式;呼叫 `WinMain` （或 `wWinMain` ），必須定義為使用**`__stdcall`**|
|**_DllMainCRTStartup**|DLL;呼叫 `DllMain` 是否存在（必須定義為使用）**`__stdcall`**|

如果未指定[/DLL](dll-build-a-dll.md)或[/SUBSYSTEM](subsystem-specify-subsystem.md)選項，則連結器會根據是否定義來選取子系統和進入點 `main` `WinMain` 。

函 `main` 式、 `WinMain` 和 `DllMain` 是使用者定義進入點的三種形式。

建立受控映射時，指定給/ENTRY 的函式必須具有（LPVOID *var1*、DWORD *var2*、LPVOID *var3*）的簽章。

如需如何定義您自己的進入點的相關資訊 `DllMain` ，請參閱[dll 和 Visual C++ 執行時間程式庫行為](../run-time-library-behavior.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [ **Advanced** ] 屬性頁。

1. 修改 [**進入點**] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
