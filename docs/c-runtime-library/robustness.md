---
title: 加強性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b76235187bad83eb638588cbbd179e93523fdf2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="robustness"></a>加強性

使用下列 C 執行階段程式庫函式加強您的程式。

## <a name="run-time-robustness-functions"></a>執行階段加強性函式

|功能|使用|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|若 **new** 運算子無法配置記憶體，則將控制項傳送至您的錯誤處理機制。|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|以 C++ 類型化例外狀況處理 Win32 例外狀況 (C 結構化例外狀況)。|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安裝要由 [terminate](../c-runtime-library/reference/terminate-crt.md) 呼叫的專屬中止函式。|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|安裝要由 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 呼叫的專屬中止函式。|

## <a name="see-also"></a>請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)<br/>
