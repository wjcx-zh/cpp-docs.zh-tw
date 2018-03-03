---
title: "-GS （緩衝區安全性檢查） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
- /GS
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e5699830a090f42feb92b24ec43fbae36634c4df
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="gs-buffer-security-check"></a>/GS (緩衝區安全性檢查)  
  
偵測到覆寫函式的傳回位址、 例外狀況處理常式的位址或特定類型的參數部分緩衝區滿溢。 造成緩衝區溢位是由駭客利用不會強制緩衝區大小限制的程式碼的技術。  
  
## <a name="syntax"></a>語法  
  
```  
/GS[-]  
```  
  
## <a name="remarks"></a>備註  
  
**/GS**預設為開啟。 如果您預期您的應用程式沒有安全性漏洞時，使用**/GS-**。 如需有關**/GS**，請參閱[編譯器安全性檢查在深度](http://go.microsoft.com/fwlink/p/?linkid=7260)。 如需隱藏緩衝區滿溢偵測的詳細資訊，請參閱[safebuffers](../../cpp/safebuffers.md)。  
  
## <a name="security-checks"></a>安全性檢查  
  
編譯器會辨識受限於緩衝區滿溢問題的函式，編譯器會配置之前傳回位址堆疊上的空間。 函式進入時，載入已配置的空間*安全性 cookie* ，在模組載入一次計算。 函式結束時，並在 64 位元作業系統上的框架回溯期間，以確定該 cookie 的值仍然是相同呼叫 helper 函式。 不同的值會指出堆疊的覆寫可能會發生。 如果偵測到不同的值時，會終止處理程序。  
  
## <a name="gs-buffers"></a>GS 緩衝區  
  
緩衝區滿溢安全性檢查對*GS 緩衝區*。 GS 緩衝區可以是下列其中一種：  
  
-   大於 4 個位元組，有兩個以上的項目和項目類型不是指標類型的陣列。  
  
-   資料結構的大小超過 8 個位元組，且不包含任何指標。  
  
-   使用所配置的緩衝區[_alloca](../../c-runtime-library/reference/alloca.md)函式。  
  
-   任何類別或結構，其中包含 GS 緩衝區。  
  
例如，下列陳述式會宣告 GS 緩衝區。  
  
```cpp  
char buffer[20];  
int buffer[20];  
struct { int a; int b; int c; int d; } myStruct;  
struct { int a; char buf[20]; };  
```  
  
不過，下列陳述式沒有宣告 GS 緩衝區。 前兩個宣告包含指標類型的項目。 第三個和第四個陳述式會宣告的陣列的大小為太小。 第五個陳述式會宣告結構的大小 x86 平台不超過 8 個位元組。  
  
```cpp  
char *pBuf[20];  
void *pv[20];  
char buf[4];  
int buf[2];  
struct { int a; int b; };  
```  
  
## <a name="initialize-the-security-cookie"></a>初始化安全性 Cookie  
  
**/GS**編譯器選項需要使用 cookie 的任何函式執行之前初始化安全性 cookie。 安全性 cookie 必須立即初始化項目可以在 EXE 或 DLL。 這在如果您使用預設 VCRuntime 進入點會自動完成： mainCRTStartup，wmainCRTStartup，WinMainCRTStartup，wWinMainCRTStartup，或 _DllMainCRTStartup。 如果您使用的替代項目點，您必須藉由呼叫，以手動方式初始化安全性 cookie [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)。  
  
## <a name="what-is-protected"></a>受保護的內容  
  
**/GS**編譯器選項可以保護下列項目：  
  
-   函式呼叫的傳回位址。  
  
-   例外狀況處理常式函式的位址。  
  
-   易受攻擊的函式參數。  
  
在所有平台， **/GS**嘗試偵測到傳回位址的緩衝區滿溢。 緩衝區滿溢是更輕鬆地利用例如 x86 和 x64，使用儲存在堆疊函式呼叫的傳回位址的呼叫慣例的平台上。  
  
在 x86，如果函式使用例外狀況處理常式，編譯器會插入安全性 cookie 保護例外狀況處理常式的位址。 在框架回溯會檢查 cookie。  
  
**/GS**保護*容易遭受參數*傳遞至函式。 易受攻擊的參數是指標，c + + 參考，C-包含的結構 （c + + POD 類型） 的指標或 GS 緩衝區。  
  
之前的 cookie 和區域變數配置有弱點的參數。 緩衝區滿溢可以覆寫這些參數。 會使用這些參數的函式中的程式碼可能會導致攻擊，此函數會傳回再執行安全性檢查。 為了降低這個危險，編譯器期間函式初構中會有弱點的參數複製，並將它們放在任何緩衝區儲存體區域下方。  
  
編譯器不會有弱點的參數的複本在下列情況：  
  
-   不會包含 GS 緩衝區的函式。  
  
-   最佳化 ([/O 選項](../../build/reference/o-options-optimize-code.md)) 未啟用。  
  
-   具有變數引數清單 （...） 的函式。  
  
-   函式，以標記[naked](../../cpp/naked-cpp.md)。  
  
-   包含內嵌組譯碼中的第一個陳述式的函式。  
  
-   參數只能用於不太可能會處於易遭利用發生緩衝區滿溢的方式。  
  
## <a name="what-is-not-protected"></a>未受保護的內容  
  
**/GS**編譯器選項不會保護所有的緩衝區滿溢安全性攻擊。 例如，如果您有緩衝區和 vtable 中的物件，緩衝區溢位可能會損毀 vtable。  
  
即使您使用**/GS**，一定要撰寫安全程式碼有任何緩衝區滿溢嘗試。  
  
### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下專案，然後按一下**屬性**。  
  
     如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在**屬性頁**對話方塊中，按一下  **C/c + +**資料夾。  
  
3.  按一下**程式碼產生**屬性頁。  
  
4.  修改**緩衝區安全性檢查**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>。  
  
## <a name="example"></a>範例  
  
這個範例會發生緩衝區滿溢。 這會導致應用程式在執行階段失敗。  
  
```C  
// compile with: /c /W1  
#include <cstring>  
#include <stdlib.h>  
#pragma warning(disable : 4996)   // for strcpy use  
  
// Vulnerable function  
void vulnerable(const char *str) {  
   char buffer[10];  
   strcpy(buffer, str); // overrun buffer !!!  
  
   // use a secure CRT function to help prevent buffer overruns  
   // truncate string to fit a 10 byte buffer  
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);  
}  
  
int main() {  
   // declare buffer that is bigger than expected  
   char large_buffer[] = "This string is longer than 10 characters!!";  
   vulnerable(large_buffer);  
}  
```  
  
## <a name="see-also"></a>請參閱  
  
[編譯器選項](../../build/reference/compiler-options.md)   
[設定編譯器選項](../../build/reference/setting-compiler-options.md)