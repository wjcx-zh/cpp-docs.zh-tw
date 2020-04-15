---
title: /CLRSUPPORTLASTERROR (保留最後的 PInvoke 呼叫錯誤碼)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 19930591c2d0406c68b1a408622a49c9e8b1d551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322267"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (保留最後的 PInvoke 呼叫錯誤碼)

**/CLRSUPPORTLASTERROR(** 預設情況下處於打開狀態)保留了通過 P/Invoke 機制調用的函數的最後錯誤代碼,該機制允許您從使用 **/clr**編譯的代碼調用 DLLS 中的本機函數。

## <a name="syntax"></a>語法

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>備註

保留最後一個錯誤代碼意味著性能下降。  如果不想對保留最後一個錯誤代碼的性能產生影響,請連結與 **/CLRSUPPORTLASTERROR:NO**。

您可以通過連結到 **/CLRSUPPORTLASTERROR:SYSTEMDLL**來最小化性能影響,後者僅保留系統 DlL 中函數的最後錯誤代碼。  系統 DLL 定義為以下之一:

|||||
|-|-|-|-|
|ACLUI.Dll|活動。Dll|ADPTIF。Dll|ADVAPI32.Dll|
|ASYCFILT.Dll|奧特赫。Dll|AVICAP32.Dll|AVIFIL32.Dll|
|內閣。Dll|CLUSAPI。Dll|COMCTL32.Dll|COMDLG32.Dll|
|COMSVCS.Dll|瑞德威Dll|CRYPT32.Dll|密碼網。Dll|
|CRYPTUI。Dll|D3D8THK.Dll|DBGENG。Dll|DBGHELP。Dll|
|DCIMAN32.Dll|DNSAPI。Dll|DSPROP.Dll|DSUIEXT.Dll|
|GDI32.Dll|GLU32.Dll|HLINK。Dll|ICM32.Dll|
|圖像HLP。Dll|IMM32.Dll|IPHLPAPI。Dll|IPROP。Dll|
|內核32.Dll|KSUSER。Dll|LOADPERF.Dll|LZ32.Dll|
|MAPI32.Dll|MGMTAPI。Dll|MOBSYNC。Dll|Mpr。Dll|
|MPRAPI。Dll|MQRT。Dll|MSACM32.Dll|MSCMS。Dll|
|微星。Dll|MSIMG32.Dll|放大縮小字型功能 放大縮小字型功能Dll|MSTASK。Dll|
|MSVFW32.Dll|姆索科克Dll|MTXEX.Dll|NDDEAPI。Dll|
|NETAPI32.Dll|NPPTOOLS。Dll|NTDSAPI。Dll|NTDSBCLI。Dll|
|NTMSAPI。Dll|ODBC32.Dll|ODBCBCP.Dll|OLE32.Dll|
|OLEACC.Dll|奧萊奧特32。Dll|OLEDLG.Dll|OPENGL32.Dll|
|Pdh。Dll|POWRPROF.Dll|QOSNAME。Dll|查詢。Dll|
|拉薩皮32。Dll|RASDLG.Dll|RASSAPI。Dll|RESUTILS。Dll|
|富德20。Dll|RPCNS4.Dll|RPCRT4.Dll|Rtm。Dll|
|RTUTILS.Dll|斯卡德格Dll|安全32。Dll|SENSAPI。Dll|
|設置API。Dll|證監會。Dll|SHELL32.Dll|舒斯裡Dll|
|SHLWAPI。Dll|SISBKUP。Dll|SNMPAPI。Dll|SRCLIENT。Dll|
|性病。Dll|TAPI32.Dll|交通。Dll|Url。Dll|
|URLMON。Dll|使用者32。Dll|USERENV.Dll|USP10.Dll|
|UXTHEME.Dll|VDMDBG。Dll|版本。Dll|溫法克斯Dll|
|溫HTTP。Dll|威尼內特Dll|溫MM。Dll|溫斯卡Dll|
|贏得信任。Dll|WLDAP32。Dll|哇32。Dll|WS2_32.DLL|
|WSNMP32.Dll|WSOCK32.DLL|WTSAPI32.Dll|XOLEHLP.Dll|

> [!NOTE]
> CLR 代碼在同一模組中使用的非託管函數不支援保留最後一個錯誤。

- 有關詳細資訊,請參閱[/clr(通用語言執行時編譯)](clr-common-language-runtime-compilation.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [命令列] **** 屬性頁。

1. 在「**附加選項**」框中鍵入該選項。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>＞。

## <a name="example"></a>範例

以下範例使用一個匯出的函數定義本機 DLL,該函數修改上次錯誤。

```cpp
// CLRSUPPORTLASTERROR_dll.cpp
// compile with: /LD
#include <windows.h>
#include <math.h>

#pragma unmanaged
__declspec(dllexport) double MySqrt(__int64 n) {
   SetLastError(DWORD(-1));
   return sqrt(double(n));
}
```

## <a name="example"></a>範例

以下範例使用 DLL,展示如何使用 **/CLRSUPPORTLASTERROR**。

```cpp
// CLRSUPPORTLASTERROR_client.cpp
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll
// processor: x86
#include <windows.h>
#include <wininet.h>
#include <stdio.h>
#include <math.h>

#pragma comment(lib, "wininet.lib")

double MySqrt(__int64 n);

#pragma managed
int main() {
   double   d = 0.0;
   __int64 n = 65;
   HANDLE  hGroup = NULL;
   GROUPID groupID;
   DWORD   dwSet = 127, dwGet = 37;

   SetLastError(dwSet);
   d = MySqrt(n);
   dwGet = GetLastError();

   if (dwGet == DWORD(-1))
      printf_s("GetLastError for application call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for application call failed (%d).\n",
             dwGet);

   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,
                           0, 0, &groupID, 0);
   dwGet = GetLastError();
   if (dwGet == 183)
      printf_s("GetLastError for system call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for system call failed (%d).\n",
             dwGet);
}
```

```Output
GetLastError for application call failed (127).
GetLastError for system call succeeded (183).
```

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
