---
title: /CLRSUPPORTLASTERROR (保留最後的 PInvoke 呼叫錯誤碼)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 64948d81759d415245e741bc6152d56bb35480d2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988346"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (保留最後的 PInvoke 呼叫錯誤碼)

**/CLRSUPPORTLASTERROR**（預設為開啟）會保留透過 P/Invoke 機制呼叫之函式的最後一個錯誤碼，這可讓您從使用 **/clr**編譯的程式碼，呼叫 dll 中的原生函式。

## <a name="syntax"></a>語法

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>備註

保留最後一個錯誤碼意味著效能降低。  如果您不想要導致保留最後一個錯誤碼的效能影響，請與 **/CLRSUPPORTLASTERROR： NO**連結。

您可以藉由連結 **/CLRSUPPORTLASTERROR： SYSTEMDLL**來將效能影響降到最低，這只會保留系統 dll 中函式的最後一個錯誤碼。  系統 DLL 會定義為下列其中一項：

|||||
|-|-|-|-|
|ACLUI.URLMON.DLL|ACTIVEDS.URLMON.DLL|ADPTIF.URLMON.DLL|ADVAPI32.DLL.URLMON.DLL|
|ASYCFILT.URLMON.DLL|授權.URLMON.DLL|AVICAP32.URLMON.DLL|AVIFIL32.URLMON.DLL|
|檔案櫃.URLMON.DLL|CLUSAPI.URLMON.DLL|COMCTL32.DLL.URLMON.DLL|COMDLG32.URLMON.DLL|
|COMSVCS.URLMON.DLL|CREDUI.URLMON.DLL|CRYPT32.DLL.URLMON.DLL|CRYPTNET.URLMON.DLL|
|CRYPTUI.DLL.URLMON.DLL|D3D8THK.URLMON.DLL|DBGENG.URLMON.DLL|DBGHELP.URLMON.DLL|
|DCIMAN32.URLMON.DLL|DNSAPI.URLMON.DLL|DSPROP.URLMON.DLL|DSUIEXT.URLMON.DLL|
|GDI32.URLMON.DLL|GLU32.URLMON.DLL|HLINK.URLMON.DLL|ICM32.URLMON.DLL|
|IMAGEHLP.DLL.URLMON.DLL|IMM32.URLMON.DLL|IPHLPAPI.URLMON.DLL|IPROP.URLMON.DLL|
|KERNEL32.DLL.URLMON.DLL|KSUSER.URLMON.DLL|LOADPERF.URLMON.DLL|LZ32.URLMON.DLL|
|MAPI32.DLL.URLMON.DLL|MGMTAPI.URLMON.DLL|MOBSYNC.URLMON.DLL|MPR.URLMON.DLL|
|MPRAPI.URLMON.DLL|MQRT.URLMON.DLL|MSACM32.URLMON.DLL|都會.URLMON.DLL|
|MSI.URLMON.DLL|MSIMG32.LIB.URLMON.DLL|MSRATING.URLMON.DLL|MSTASK.URLMON.DLL|
|MSVFW32.URLMON.DLL|MSWSOCK.URLMON.DLL|MTXEX.URLMON.DLL|NDDEAPI.URLMON.DLL|
|NETAPI32.URLMON.DLL|NPPTOOLS.URLMON.DLL|NTDSAPI.URLMON.DLL|NTDSBCLI.URLMON.DLL|
|NTMSAPI.URLMON.DLL|ODBC32.LIB.URLMON.DLL|ODBCBCP.DLL.URLMON.DLL|OLE32.LIB.URLMON.DLL|
|OLEACC.URLMON.DLL|OLEAUT32.LIB.URLMON.DLL|OLEDLG.URLMON.DLL|OPENGL32.URLMON.DLL|
|PDH.URLMON.DLL|POWRPROF.URLMON.DLL|QOSNAME.URLMON.DLL|查詢.URLMON.DLL|
|RASAPI32.URLMON.DLL|RASDLG.URLMON.DLL|RASSAPI.URLMON.DLL|RESUTILS.URLMON.DLL|
|RICHED20.DLL.URLMON.DLL|RPCNS4.URLMON.DLL|RPCRT4.URLMON.DLL|RTM.URLMON.DLL|
|RTUTILS.URLMON.DLL|SCARDDLG.URLMON.DLL|SECUR32.URLMON.DLL|SENSAPI.URLMON.DLL|
|SETUPAPI.LOG.URLMON.DLL|SFC.URLMON.DLL|SHELL32.URLMON.DLL|SHFOLDER.DLL.URLMON.DLL|
|SHLWAPI.URLMON.DLL|SISBKUP.URLMON.DLL|SNMPAPI.URLMON.DLL|SRCLIENT.URLMON.DLL|
|STI.URLMON.DLL|TAPI32.URLMON.DLL|流量.URLMON.DLL|連結.URLMON.DLL|
|URLMON.DLL.URLMON.DLL|USER32.URLMON.DLL|USERENV.URLMON.DLL|USP10.URLMON.DLL|
|UXTHEME.URLMON.DLL|VDMDBG.URLMON.DLL|版本。URLMON.DLL|WINFAX.URLMON.DLL|
|WINHTTP.URLMON.DLL|WININET.URLMON.DLL|WINMM.DLL.URLMON.DLL|WINSCARD.URLMON.DLL|
|WINTRUST.URLMON.DLL|WLDAP32.DLL.URLMON.DLL|WOW32.URLMON.DLL|WS2_32 .DLL|
|WSNMP32.DLL.URLMON.DLL|WSOCK32.DLL|WTSAPI32.DLL.URLMON.DLL|XOLEHLP.URLMON.DLL|

> [!NOTE]
>  在相同的模組中，CLR 程式碼所使用的非受控函式不支援保留最後一個錯誤。

- 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](clr-common-language-runtime-compilation.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [命令列] 屬性頁。

1. 在 [**其他選項**] 方塊中輸入選項。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>範例

下列範例會定義具有一個匯出函式的原生 DLL，以修改最後一個錯誤。

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

下列範例會取用 DLL，示範如何使用 **/CLRSUPPORTLASTERROR**。

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

## <a name="see-also"></a>請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
