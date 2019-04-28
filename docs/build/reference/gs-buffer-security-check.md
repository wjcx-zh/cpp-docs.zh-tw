---
title: /GS (緩衝區安全性檢查)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
- /GS
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 10afa874092eb563903ba5f49c6add136afc869c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292168"
---
# <a name="gs-buffer-security-check"></a>/GS (緩衝區安全性檢查)

偵測到某些緩衝區溢位，覆寫函式的傳回位址、 例外狀況處理常式的位址或特定類型的參數。 造成緩衝區溢位是駭客用來惡意探索不會強制使用的緩衝區大小限制的程式碼的技術。

## <a name="syntax"></a>語法

```
/GS[-]
```

## <a name="remarks"></a>備註

**/GS**預設為開啟。 如果您預期您的應用程式沒有安全性漏洞時，使用 **/GS-**。 如需隱藏緩衝區滿溢偵測的詳細資訊，請參閱[safebuffers](../../cpp/safebuffers.md)。

## <a name="security-checks"></a>安全性檢查

編譯器會辨識受限於緩衝區滿溢問題的函式，則編譯器會配置之前的傳回位址在堆疊上的空間。 函式項目，配置的空間會載入*安全性 cookie* ，會計算一次在模組載入。 函式結束時，並在 64 位元作業系統上的框架回溯期間，會呼叫 helper 函式可確定 cookie 的值仍然相同。 不同的值會指出堆疊的覆寫可能會發生。 如果偵測到不同的值時，會終止處理程序。

## <a name="gs-buffers"></a>GS 緩衝區

緩衝區滿溢安全性檢查對*GS 緩衝區*。 GS 緩衝區可以是下列其中一種：

- 陣列大於 4 個位元組，有兩個以上的項目，且不是指標類型的項目類型。

- 一種資料結構的大小為超過 8 個位元組，並不包含任何指標。

- 使用所配置的緩衝區[_alloca](../../c-runtime-library/reference/alloca.md)函式。

- 任何類別或結構，其中包含 GS 緩衝區。

例如，下列陳述式會宣告 GS 緩衝區。

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

不過，下列陳述式未宣告 GS 緩衝區。 前兩個宣告包含指標類型的項目。 第三個和第四個陳述式會宣告的陣列大小是太小。 第五個陳述式宣告的結構大小 x86 平台不超過 8 個位元組。

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>初始化安全性 Cookie

**/GS**編譯器選項可讓您需要執行任何會使用 cookie 的函式之前，先初始化安全性 cookie。 安全性 cookie 必須立即初始化，項目，以在 EXE 或 DLL。 這在如果您使用預設 VCRuntime 進入點會自動完成： mainCRTStartup，wmainCRTStartup，WinMainCRTStartup，wWinMainCRTStartup，或 _DllMainCRTStartup。 如果您使用替代的進入點時，您必須藉由呼叫，以手動方式初始化安全性 cookie [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)。

## <a name="what-is-protected"></a>受保護的內容

**/GS**編譯器選項可以保護下列項目：

- 函式呼叫的傳回位址。

- 例外狀況處理常式函式的位址。

- 易受攻擊的函式參數。

所有的平台上 **/GS**嘗試偵測到的傳回位址的緩衝區溢位。 緩衝區溢位會更輕鬆地利用 x86 和 x64，使用儲存在堆疊的函式呼叫的傳回位址的呼叫慣例等平台上。

在 x86 上如果函式使用的例外狀況處理常式中，編譯器會插入安全性 cookie 來保護例外狀況處理常式的位址。 在框架回溯會檢查 cookie。

**/GS**保護*易受攻擊參數*，會傳遞至函式。 有弱點的參數是指標，C++參考，C 結構 (C++的 POD 類型)，其中包含的指標或 GS 的緩衝區。

之前的 cookie 和區域變數配置有弱點的參數。 緩衝區溢位可能會覆寫這些參數。 會使用這些參數的函式中的程式碼可能會導致攻擊，此函數會傳回並執行安全性檢查。 若要降低此風險，編譯器會建立一份有弱點的參數，在函式初構期間，並將它們放在下列任何緩衝區的儲存體區域。

編譯器不會在下列情況下進行複製的有弱點的參數：

- 沒有 GS 緩衝區的函式。

- 最佳化 ([/O 選項](o-options-optimize-code.md)) 不會啟用。

- 具有變數引數清單 （...） 的函式。

- 函式標記著[naked](../../cpp/naked-cpp.md)。

- 包含內嵌組譯碼中的第一個陳述式的函式。

- 參數只能用於不太可能會發生緩衝區滿溢的情況時可利用來攻擊的方式。

## <a name="what-is-not-protected"></a>未受保護的內容

**/GS**編譯器選項不會保護所有的緩衝區滿溢安全性攻擊。 例如，如果您有緩衝區和 vtable 中的物件時，緩衝區滿溢的情況可能會損毀 vtable。

即使您使用 **/GS**，不斷地嘗試撰寫安全程式碼有無緩衝區溢位。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 在 **方案總管**，以滑鼠右鍵按一下專案，然後按一下**屬性**。

   如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 在 [**屬性頁**] 對話方塊中，按一下**C /C++** 資料夾。

1. 按一下 **程式碼產生**屬性頁。

1. 修改**緩衝區安全性檢查**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>。

## <a name="example"></a>範例

此範例中會發生緩衝區滿溢。 這會導致應用程式在執行階段失敗。

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

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
