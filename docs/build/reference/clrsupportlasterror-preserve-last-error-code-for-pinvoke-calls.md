---
title: "/CLRSUPPORTLASTERROR (保留最後的 PInvoke 呼叫錯誤碼) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRSUPPORTLASTERROR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRSUPPORTLASTERROR 連結器選項"
  - "-CLRSUPPORTLASTERROR 連結器選項"
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRSUPPORTLASTERROR (保留最後的 PInvoke 呼叫錯誤碼)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/CLRSUPPORTLASTERROR** 預設為開啟，會保留透過 P\/Invoke 機制 \(可以讓您從以 **\/clr** 編譯的程式碼，在 DLL 中呼叫原生函式\) 所呼叫函式的最後錯誤碼。  
  
## 語法  
  
```  
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}  
```  
  
## 備註  
 保留最後的錯誤碼意味著效能的降低。如果您不想要因為保留最後錯誤碼而影響效能的情況發生，請與 **\/CLRSUPPORTLASTERROR:NO** 連結。  
  
 您可以與 **\/CLRSUPPORTLASTERROR:SYSTEMDLL** 連結 \(只會保留系統 DLL 中函式的最後錯誤碼\)，藉此將效能影響降到最低。系統 DLL 會定義下列其中一項：  
  
|||||  
|-|-|-|-|  
|ACLUI.DLL|ACTIVEDS.DLL|ADPTIF.DLL|ADVAPI32.DLL|  
|ASYCFILT.DLL|AUTHZ.DLL|AVICAP32.DLL|AVIFIL32.DLL|  
|CABINET.DLL|CLUSAPI.DLL|COMCTL32.DLL|COMDLG32.DLL|  
|COMSVCS.DLL|CREDUI.DLL|CRYPT32.DLL|CRYPTNET.DLL|  
|CRYPTUI.DLL|D3D8THK.DLL|DBGENG.DLL|DBGHELP.DLL|  
|DCIMAN32.DLL|DNSAPI.DLL|DSPROP.DLL|DSUIEXT.DLL|  
|GDI32.DLL|GLU32.DLL|HLINK.DLL|ICM32.DLL|  
|IMAGEHLP.DLL|IMM32.DLL|IPHLPAPI.DLL|IPROP.DLL|  
|KERNEL32.DLL|KSUSER.DLL|LOADPERF.DLL|LZ32.DLL|  
|MAPI32.DLL|MGMTAPI.DLL|MOBSYNC.DLL|MPR.DLL|  
|MPRAPI.DLL|MQRT.DLL|MSACM32.DLL|MSCMS.DLL|  
|MSI.DLL|MSIMG32.DLL|MSRATING.DLL|MSTASK.DLL|  
|MSVFW32.DLL|MSWSOCK.DLL|MTXEX.DLL|NDDEAPI.DLL|  
|NETAPI32.DLL|NPPTOOLS.DLL|NTDSAPI.DLL|NTDSBCLI.DLL|  
|NTMSAPI.DLL|ODBC32.DLL|ODBCBCP.DLL|OLE32.DLL|  
|OLEACC.DLL|OLEAUT32.DLL|OLEDLG.DLL|OPENGL32.DLL|  
|PDH.DLL|POWRPROF.DLL|QOSNAME.DLL|QUERY.DLL|  
|RASAPI32.DLL|RASDLG.DLL|RASSAPI.DLL|RESUTILS.DLL|  
|RICHED20.DLL|RPCNS4.DLL|RPCRT4.DLL|RTM.DLL|  
|RTUTILS.DLL|SCARDDLG.DLL|SECUR32.DLL|SENSAPI.DLL|  
|SETUPAPI.DLL|SFC.DLL|SHELL32.DLL|SHFOLDER.DLL|  
|SHLWAPI.DLL|SISBKUP.DLL|SNMPAPI.DLL|SRCLIENT.DLL|  
|STI.DLL|TAPI32.DLL|TRAFFIC.DLL|URL.DLL|  
|URLMON.DLL|USER32.DLL|USERENV.DLL|USP10.DLL|  
|UXTHEME.DLL|VDMDBG.DLL|VERSION.DLL|WINFAX.DLL|  
|WINHTTP.DLL|WININET.DLL|WINMM.DLL|WINSCARD.DLL|  
|WINTRUST.DLL|WLDAP32.DLL|WOW32.DLL|WS2\_32.DLL|  
|WSNMP32.DLL|WSOCK32.DLL|WTSAPI32.DLL|XOLEHLP.DLL|  
  
> [!NOTE]
>  相同模組中，CLR 程式碼所使用的 Unmanaged 函式不支援保留最後的錯誤。  
  
-   如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 範例  
 下面的範例會利用修改最後錯誤的匯出函式定義原生 DLL。  
  
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
  
## 範例  
 下面的範例使用 DLL，示範 **\/CLRSUPPORTLASTERROR** 的使用方法。  
  
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
  
  **應用程式呼叫的 GetLastError 失敗 \(127\)。**  
**系統呼叫的 GetLastError 成功 \(183\)。**   
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)