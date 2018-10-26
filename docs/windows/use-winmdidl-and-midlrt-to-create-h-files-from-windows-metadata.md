---
title: 如何： 使用 winmdidl.exe 和 midlrt.exe windows 中繼資料建立.h 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f97ef0f285cda7d31ddd53f0a8b0ca9a22f360c
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136194"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>如何：使用 winmdidl.exe 和 midlrt.exe 根據 Windows 中繼資料建立 .h 檔案

Winmdidl.exe 和 midlrt.exe 啟用原生 C++ 程式碼與 Windows 執行階段元件之間的 COM 層級互動。 Winmdidl.exe 會輸入包含 Windows 執行階段元件之中繼資料的 .winmd 檔案，並輸出 IDL 檔案。 Midlrt.exe 會將該 IDL 檔案轉換成 C++ 程式碼可以取用的標頭檔。 這兩個工具都是在命令列上執行。

您可以在兩個主要案例中使用這些工具：

- 建立自訂的 IDL 和標頭檔，讓使用 Windows 執行階段範本程式庫 (WRL) 所撰寫的 C++ 應用程式可以使用自訂的 Windows 執行階段元件。

- 為 Windows 執行階段元件中的使用者定義的事件類型，產生 Proxy 和虛設常式檔案。 如需詳細資訊，請參閱 <<c0> [ 自訂事件和事件存取子，在 Windows 執行階段元件](/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components)。

這些工具僅適用於剖析自訂的 .winmd 檔案。 已為您產生 Windows 作業系統元件的 .idl 和 .h 檔案。 根據預設，在 Windows 8.1，它們位於 \Program 檔案 (x86) \Windows Kits\8.1\Include\winrt\\。

## <a name="location-of-the-tools"></a>工具的位置

根據預設，在 [Windows 8.1 中，winmdidl.exe 和 midlrt.exe 位於 C:\Program Files (x86) \Windows Kits\8.1\\。 工具的版本也可在 \bin\x86\ 和 \bin\x64\ 資料夾中取得。

## <a name="winmdidl-command-line-arguments"></a>Winmdidl 命令列引數

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
防止主控台顯示 winmdidl 著作權訊息和版本號碼。

**/suppressversioncheck**<br/>
未使用。

**/ 時間**<br/>
在主控台輸出中顯示總執行時間。

**/outdir:**<em>dir</em><br/>
指定輸出目錄。 如果路徑包含空格，請使用引號。 預設的輸出目錄*\<磁碟機 >*: \Users\\*\<使用者名稱 >* \AppData\Local\VirtualStore\Program 檔案 (x86) \Microsoft VisualStudio 12.0\\。

**/ 橫幅：**<em>檔案</em><br/>
指定包含要在預設著作權訊息前面加上自訂文字，以及在產生的 .idl 檔案頂端加上 winmdidl 版本號碼的檔案。 如果路徑包含空格，請使用引號。

**/utf8**<br/>
造成檔案格式化為 UTF-8。

*其 Winmdfile*<br/>
要剖析的 .winmd 檔案名稱。 如果路徑包含空格，請使用引號。

## <a name="midlrt-command-line-arguments"></a>Midlrt 命令列引數

請參閱[MIDLRT 和 Windows 執行階段元件](/windows/desktop/Midl/midlrt-and-windows-runtime-components)。

## <a name="examples"></a>範例

下列範例會在 Visual Studio x86 命令提示字元上顯示 winmdidl 命令。 它會指定輸出目錄，和包含新增至產生的 .idl 檔案之特殊橫幅文字的檔案。

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

下一個範例顯示 winmdidl 的主控台畫面，指出作業已成功。

**產生 c:\users\giraffe\documents\\\Test_for_winmdidl.idl**

接下來，midlrt 在產生的 IDL 檔案上執行。 請注意， **/metadata_dir** .idl 檔的名稱之後指定引數。 \WinMetadata\ 的路徑是必要的，它是 windows.winmd 的位置。

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>備註

winmdidl 作業的輸出檔案與輸入檔案具有相同的名稱，但具有 .idl 副檔名。

如果您正在開發將從 WRL 存取的 Windows 執行階段元件，您可以指定 winmdidl.exe 和 midlrt.exe 做為建置後步驟執行，以便在每個建置中產生 .idl 和 .h 檔案。 如需範例，請參閱[在 Windows 執行階段元件中引發事件](/uwp/winrt-components/raising-events-in-windows-runtime-components)。