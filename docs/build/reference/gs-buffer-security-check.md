---
title: /GS (緩衝區安全性檢查)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 92d296e8079a9ecd8d366c46bbdad8b2ee5dc313
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439571"
---
# <a name="gs-buffer-security-check"></a>/GS (緩衝區安全性檢查)

偵測一些會覆寫函式的傳回位址、例外狀況處理常式位址或特定類型參數的緩衝區溢位。 造成緩衝區溢位是駭客用來入侵不會強制執行緩衝區大小限制之程式碼的技術。

## <a name="syntax"></a>語法

```
/GS[-]
```

## <a name="remarks"></a>備註

**/Gs**預設為開啟。 如果您預期應用程式沒有任何安全性風險，請使用 **/GS-** 。 如需隱藏緩衝區溢位偵測的詳細資訊，請參閱[safebuffers](../../cpp/safebuffers.md)。

## <a name="security-checks"></a>安全性檢查

在編譯器可辨識為緩衝區溢位問題的函式上，編譯器會在傳回位址之前，于堆疊上配置空間。 在函式專案上，已配置的空間會使用在模組載入時所計算一次的*安全性 cookie*來載入。 在函式結束時，以及在64位作業系統上的框架回溯期間，會呼叫 helper 函數，以確保 cookie 的值仍然相同。 另一個值表示可能發生了堆疊的覆寫。 如果偵測到不同的值，進程就會終止。

## <a name="gs-buffers"></a>GS 緩衝區

緩衝區溢位安全性檢查會在*GS 緩衝區*上執行。 GS 緩衝區可以是下列其中一種：

- 大於4個位元組的陣列具有兩個以上的元素，而且具有不是指標類型的元素類型。

- 大小超過8個位元組且不包含任何指標的資料結構。

- 使用[_alloca](../../c-runtime-library/reference/alloca.md)函數配置的緩衝區。

- 包含 GS 緩衝區的任何類別或結構。

例如，下列語句會宣告 GS 緩衝區。

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

不過，下列語句不會宣告 GS 緩衝區。 前兩個宣告包含指標類型的元素。 第三個和第四個語句會宣告大小太小的陣列。 第五個語句宣告的結構，其大小在 x86 平臺上不超過8個位元組。

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>初始化安全性 Cookie

**/Gs**編譯器選項需要在執行任何使用 cookie 的函式之前，先初始化安全性 cookie。 在進入 EXE 或 DLL 時，必須立即初始化安全性 cookie。 如果您使用預設的 VCRuntime 進入點，則會自動完成此動作： mainCRTStartup、wmainCRTStartup、WinMainCRTStartup、wWinMainCRTStartup 或 _DllMainCRTStartup。 如果您使用替代的進入點，則必須藉由呼叫[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)，手動初始化安全性 cookie。

## <a name="what-is-protected"></a>受保護的內容

**/Gs**編譯器選項可保護下列專案：

- 函式呼叫的傳回位址。

- 函式的例外狀況處理常式的位址。

- 易受攻擊的函式參數。

在所有平臺上， **/gs**會嘗試偵測到傳回位址的緩衝區溢位。 緩衝區溢位在 x86 和 x64 等平臺上更容易受到攻擊，其使用呼叫慣例來儲存堆疊上函式呼叫的傳回位址。

在 x86 上，如果函式使用例外狀況處理常式，則編譯器會插入安全性 cookie 來保護例外狀況處理常式的位址。 在框架回溯期間會檢查 cookie。

**/Gs**會保護傳遞至函式的*易受攻擊參數*。 易受攻擊的參數是指標、 C++參考、包含指標的 C 結構C++ （POD 類型），或是 GS 緩衝區。

易受攻擊的參數會在 cookie 和本機變數之前配置。 緩衝區溢位可能會覆寫這些參數。 而在函式中使用這些參數的程式碼，可能會在函式傳回並執行安全性檢查之前造成攻擊。 為了將此危險降到最低，編譯器會在函式初構期間建立易受攻擊的參數複本，並將它們放在任何緩衝區的儲存區域下方。

在下列情況下，編譯器不會製作易受攻擊的參數複本：

- 未包含 GS 緩衝區的函式。

- 優化（[/o 選項](o-options-optimize-code.md)）未啟用。

- 具有可變引數清單（...）的函數。

- 以[naked](../../cpp/naked-cpp.md)標記的函式。

- 在第一個語句中包含內嵌組解碼程式碼的函數。

- 只有在緩衝區溢位的情況中，才會使用較不可能被利用的方法來使用參數。

## <a name="what-is-not-protected"></a>未受保護的內容

**/Gs**編譯器選項無法防止所有緩衝區溢位的安全性攻擊。 例如，如果您在物件中有緩衝區和 vtable，緩衝區溢位可能會損毀 vtable。

即使您使用 **/gs**，一律會嘗試撰寫沒有緩衝區溢位的安全程式碼。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 在**方案總管**中，以滑鼠右鍵按一下專案，然後按一下 [**屬性**]。

   如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在 [**屬性頁**] 對話方塊中，按一下 [ **CC++ /** ] 資料夾。

1. 按一下 [程式**代碼產生**] 屬性頁。

1. 修改 [**緩衝區安全性檢查**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>＞。

## <a name="example"></a>範例

這個範例會溢出緩衝區。 這會導致應用程式在執行時間失敗。

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
