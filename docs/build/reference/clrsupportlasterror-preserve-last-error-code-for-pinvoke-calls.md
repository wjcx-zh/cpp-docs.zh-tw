---
title: "-CLRSUPPORTLASTERROR （保留最後一個錯誤碼的 PInvoke 呼叫） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /CLRSUPPORTLASTERROR
dev_langs: C++
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e082637e25832c5c5036910f7b67aff53d867bdb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (保留最後的 PInvoke 呼叫錯誤碼)
**/CLRSUPPORTLASTERROR**、 其預設為開啟，可保留透過 P/Invoke 機制，可讓您從程式碼呼叫 DLL 中的原生函式呼叫的函式的最後一個錯誤碼編譯與**/clr**。  
  
## <a name="syntax"></a>語法  
  
```  
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}  
```  
  
## <a name="remarks"></a>備註  
 保留的最後一個錯誤碼表示效能降低。  如果您不希望帶來的效能影響保留最後一個錯誤碼，以連結**/CLRSUPPORTLASTERROR:NO**。  
  
 您可以最小化的效能影響連結**/CLRSUPPORTLASTERROR:SYSTEMDLL**，只會為函式的最後一個錯誤碼保留在系統 Dll。  系統 DLL 被定義為下列其中一項：  
  
|||||  
|-|-|-|-|  
|ACLUI。DLL|ACTIVEDS。DLL|ADPTIF。DLL|ADVAPI32。DLL|  
|ASYCFILT。DLL|AUTHZ。DLL|AVICAP32。DLL|AVIFIL32。DLL|  
|封包。DLL|CLUSAPI。DLL|COMCTL32。DLL|COMDLG32。DLL|  
|COMSVCS。DLL|CREDUI。DLL|CRYPT32。DLL|CRYPTNET。DLL|  
|CRYPTUI。DLL|D3D8THK。DLL|DBGENG。DLL|DBGHELP。DLL|  
|DCIMAN32。DLL|DNSAPI。DLL|DSPROP。DLL|DSUIEXT。DLL|  
|GDI32。DLL|GLU32。DLL|HLINK。DLL|ICM32。DLL|  
|IMAGEHLP。DLL|IMM32。DLL|IPHLPAPI。DLL|IPROP。DLL|  
|KERNEL32。DLL|KSUSER。DLL|LOADPERF。DLL|LZ32。DLL|  
|MAPI32。DLL|MGMTAPI。DLL|MOBSYNC。DLL|MPR。DLL|  
|MPRAPI。DLL|MQRT。DLL|MSACM32。DLL|MSCMS。DLL|  
|MSI。DLL|MSIMG32。DLL|MSRATING。DLL|MSTASK。DLL|  
|MSVFW32。DLL|MSWSOCK。DLL|MTXEX。DLL|NDDEAPI。DLL|  
|NETAPI32。DLL|NPPTOOLS。DLL|NTDSAPI。DLL|NTDSBCLI。DLL|  
|NTMSAPI。DLL|ODBC32。DLL|ODBCBCP。DLL|OLE32。DLL|  
|OLEACC。DLL|OLEAUT32。DLL|OLEDLG。DLL|OPENGL32。DLL|  
|PDH。DLL|POWRPROF。DLL|QOSNAME。DLL|查詢。DLL|  
|RASAPI32。DLL|RASDLG。DLL|RASSAPI。DLL|RESUTILS。DLL|  
|RICHED20。DLL|RPCNS4。DLL|RPCRT4。DLL|RTM。DLL|  
|RTUTILS。DLL|SCARDDLG。DLL|SECUR32。DLL|SENSAPI。DLL|  
|SETUPAPI。DLL|SFC。DLL|SHELL32。DLL|SHFOLDER。DLL|  
|SHLWAPI。DLL|SISBKUP。DLL|SNMPAPI。DLL|SRCLIENT。DLL|  
|STI。DLL|TAPI32。DLL|流量。DLL|URL。DLL|  
|URLMON。DLL|USER32。DLL|USERENV。DLL|USP10。DLL|  
|UXTHEME。DLL|VDMDBG。DLL|版本。DLL|傳真。DLL|  
|WINHTTP。DLL|WININET。DLL|WINMM。DLL|WINSCARD。DLL|  
|WINTRUST。DLL|WLDAP32。DLL|WOW32。DLL|WS2_32.DLL|  
|WSNMP32。DLL|WSOCK32.DLL|WTSAPI32。DLL|XOLEHLP。DLL|  
  
> [!NOTE]
>  CLR 程式碼，在相同模組中所使用的 unmanaged 函式不支援保留最後一個錯誤。  
  
-   如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="example"></a>範例  
 下列範例會定義與一個匯出的函式會修改上一個錯誤的原生 DLL。  
  
```  
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
 下列範例會使用 DLL，示範如何使用**/CLRSUPPORTLASTERROR**。  
  
```  
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
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)