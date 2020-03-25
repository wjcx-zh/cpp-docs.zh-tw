---
title: 嚴重錯誤 C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: af43ddb83e872762f720b156644e0d466957a8a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203875"
---
# <a name="fatal-error-c1092"></a>嚴重錯誤 C1092

編輯後繼續不支援對資料類型的變更; 需要先進行建置

自從上次成功組建之後，您已變更或加入資料類型。

- [編輯後繼續] 不支援變更現有的資料類型，包括類別、結構或列舉定義。 您必須停止偵測並建立應用程式。

- 如果程式資料庫檔案（例如 vc*x*0 .pdb （其中*x*是使用中的視覺效果C++主要版本）是唯讀的，[編輯後繼續] 不支援加入新的資料類型。 若要加入資料類型，編譯器必須以寫入模式開啟 .pdb 檔案。

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>若要移除此錯誤而不結束目前的 debug 會話

1. 請將資料類型改回錯誤之前的狀態。

1. 從 [偵錯] 功能表選擇 [套用程式碼變更]。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>移除這個錯誤，而不變更您的原始程式碼

1. 從 [偵錯] 功能表選擇 [停止偵錯]。

1. 從 [建置] 功能表選擇 [建置]。

如需詳細資訊，請參閱 [支援的程式碼變更](/visualstudio/debugger/supported-code-changes-cpp)。
