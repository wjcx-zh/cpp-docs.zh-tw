---
title: 引發軟體例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
ms.openlocfilehash: 49ee800bafff017c29b73c5f6fd64318009a140a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562041"
---
# <a name="raising-software-exceptions"></a>引發軟體例外狀況

某些常見的程式錯誤來源是系統未標示為例外狀況。 例如，如果您嘗試配置記憶體區塊，但是沒有足夠的記憶體，執行階段或 API 函式不會引發例外狀況，而是傳回錯誤碼。

不過，您可以將任何條件視為例外狀況偵測該情況，進而在您的程式碼中，然後再呼叫報告[RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552)函式。 以這種方式標幟錯誤，您就可以將結構化例外狀況處理的優點運用到任何類型的執行階段錯誤。

若要使用結構化例外狀況處理錯誤：

- 定義您自己的事件例外狀況代碼。

- 呼叫`RaiseException`時偵測到問題時。

- 使用例外狀況處理篩選條件測試您所定義的例外狀況代碼。

\<Winerror.h > 檔案會顯示例外狀況代碼的格式。 為確保您定義的代碼不會與現有的例外狀況代碼發生衝突，請將第三個最高有效位元設為 1。 四個最高有效位元都應該依照下表所示進行設定。

|Bits|建議的二進位設定|描述|
|----------|--------------------------------|-----------------|
|31-30|11|這兩個位元負責描述程式碼的基本狀態：11 = 錯誤、00 = 成功、01 = 告知性、10 = 警告。|
|29|1|用戶端位元。 設為 1，表示使用者定義的程式碼。|
|28|0|保留位元  (保持設為 0)。|

您可以將前兩個位元設定為 11 二進位以外的設定 (如果您想要這樣做)，不過「錯誤」設定適用於大部分例外狀況。 重要的是，記得依照上表所示設定位元 29 和 28。

產生的錯誤程式碼應該因此會有最高的四個位元設為十六進位 e。比方說，下列定義會定義與任何 Windows 例外狀況代碼，不會衝突例外狀況代碼。 (不過，您可能需要查看協力廠商 DLL 使用哪些代碼)。

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

定義例外狀況代碼之後，就可以用它來引發例外狀況。 例如，下列程式碼會引發`STATUS_INSUFFICIENT_MEM`例外狀況以回應記憶體配置問題：

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

如果您只想要引發例外狀況，可以將最後三個參數設為 0。 在傳遞額外資訊以及設定旗標防止處理常式繼續執行時，最後三個參數會很有用。 請參閱[RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552)函式，如需詳細資訊的 Windows SDK 中。

然後就可以在您的例外狀況處理篩選條件中，測試您所定義的代碼。 例如: 

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>另請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)