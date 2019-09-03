---
title: __fastfail
ms.date: 09/02/2019
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: 34198409c6a57eb494bfe819b367b71405a84e64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222192"
---
# <a name="__fastfail"></a>__fastfail

**Microsoft 專屬**

立即終止額外負荷最小的呼叫處理序。

## <a name="syntax"></a>語法

```C
void __fastfail(unsigned int code);
```

### <a name="parameters"></a>參數

*錯誤碼*\
在來自 winnt 或 wdm 的符號常數,表示進程終止的原因。`FAST_FAIL_<description>`

## <a name="return-value"></a>傳回值

`__fastfail` 內建函式不會返回。

## <a name="remarks"></a>備註

內建提供*快速失敗*要求的機制, 也就是可能已損毀的進程要求立即進程終止的方式。 `__fastfail` 一般例外狀況處理功能無法處理程式狀態可能已損毀和超越堆疊復原的嚴重失敗。 使用 `__fastfail` 終止使用最少額外負荷的處理序。

在內部方面，會使用數種架構特定機制來實作 `__fastfail`：

|架構|指令|程式碼引數的位置|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|`ecx`|
|X64|int 0x29|`rcx`|
|ARM|Opcode 0xDEFB|`r0`|
|ARM64|Opcode 0xF003|`x0`|

快速失敗要求是獨立的，通常僅需要執行兩個指令。 執行快速失敗要求之後, 核心就會採取適當的動作。 在使用者模式程式碼中，當引發快速失敗事件時，沒有超出指令指標本身的記憶體相依性。 這可將其可靠性最大化, 即使發生嚴重的記憶體損毀也一樣。

引數 (winnt. h `FAST_FAIL_<description>`或 wdm 的其中一個符號常數) 描述失敗條件的類型。 `code` 它會以環境特定的方式併入失敗報告中。

使用者模式快速失敗要求會顯示為第二個機會非持續性例外狀況, 其中包含例外狀況程式碼 0xC0000409, 而且至少有一個例外狀況參數。 第一個例外狀況參數是 `code` 值。 這個例外狀況程式碼會向 Windows 錯誤報告 (WER) 和偵測基礎結構指出進程已損毀, 而且應該採取最少的同進程動作來回應失敗。 核心模式快速失敗要求是藉由使用專用的檢查錯誤程式碼 `KERNEL_SECURITY_CHECK_FAILURE`(0x139) 來實作。 在這兩種情況下，都不會叫用例外狀況處理常式，因為是預期程式要處於損毀的狀態。 如果有偵錯工具, 在終止之前, 會有機會檢查程式的狀態。

從 Windows 8 開始支援原生快速失敗機制。 原本不支援快速失敗指令的 Windows 作業系統, 通常會將快速失敗要求視為存取違規, 或做為`UNEXPECTED_KERNEL_MODE_TRAP`錯誤檢查。 在這些情況下，此程式仍然會終止，但不一定會快速終止。

`__fastfail` 僅可作為內建函式使用。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__fastfail`|x86、x64、ARM、ARM64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
