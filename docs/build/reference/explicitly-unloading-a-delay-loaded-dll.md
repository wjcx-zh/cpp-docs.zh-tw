---
title: 明確卸載延遲載入的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
ms.openlocfilehash: f661694dd791ed8db3cd9f5b72a021c7470d17f3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420449"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>明確卸載延遲載入的 DLL

[/延遲](../../build/reference/delay-delay-load-import-settings.md): unload 連結器選項可讓您卸載已延遲載入 DLL。 根據預設，當您的程式碼卸載 DLL (使用 /delay: unload 並 **__FUnloadDelayLoadedDLL2**)，延遲載入匯入保留在匯入位址表 (IAT)。 不過，如果您使用 /delay: unload 連結器命令列上，helper 函式會支援明確卸載 DLL，重設成其原始形式; 的 IAT現在無效指標將會覆寫。 IAT 是中的欄位[ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md)其中包含一份原始 IAT 的位址 （若有的話）。

## <a name="example"></a>範例

### <a name="code"></a>程式碼

```
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD
#include <windows.h>
#include <delayimp.h>
#include "MyDll.h"
#include <stdio.h>

#pragma comment(lib, "delayimp")
#pragma comment(lib, "MyDll")
int main()
{
    BOOL TestReturn;
    // MyDLL.DLL will load at this point
    fnMyDll();

    //MyDLL.dll will unload at this point
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");

    if (TestReturn)
        printf_s("\nDLL was unloaded");
    else
        printf_s("\nDLL was not unloaded");
}
```

### <a name="comments"></a>註解

卸載延遲載入 DLL 的重要注意事項：

- 您可以找到的實作 **__FUnloadDelayLoadedDLL2**檔案中的函式 \VC7\INCLUDE\DELAYHLP。CPP。

- Name 參數 **__FUnloadDelayLoadedDLL2**函式必須完全符合 （包括大小寫） 包含哪些內容匯入程式庫 （即字串也匯入資料表中的映像）。 您可以檢視與匯入程式庫的內容[DUMPBIN /DEPENDENTS](../../build/reference/dependents.md)。 如果想要使用不區分大小寫的字串相符項目，您可以更新 **__FUnloadDelayLoadedDLL2**使用其中一個 CRT 字串函式或以 Windows API 呼叫。

請參閱[卸載延遲載入 DLL](../../build/reference/unloading-a-delay-loaded-dll.md)如需詳細資訊。

## <a name="see-also"></a>另請參閱

[延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)
