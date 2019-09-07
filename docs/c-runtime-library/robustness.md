---
title: 加強性
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 108b4c9dde08adf1a3c54c810f68be69bf150472
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739606"
---
# <a name="robustness"></a>加強性

使用下列 C 執行階段程式庫函式加強您的程式。

## <a name="run-time-robustness-functions"></a>執行階段加強性函式

|函數|使用|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|若 **new** 運算子無法配置記憶體，則將控制項傳送至您的錯誤處理機制。|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|以 C++ 類型化例外狀況處理 Win32 例外狀況 (C 結構化例外狀況)。|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安裝要由 [terminate](../c-runtime-library/reference/terminate-crt.md) 呼叫的專屬中止函式。|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|安裝要由 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 呼叫的專屬中止函式。|

## <a name="see-also"></a>另請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
