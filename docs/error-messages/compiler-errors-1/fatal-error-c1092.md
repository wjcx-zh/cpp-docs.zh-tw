---
title: 嚴重錯誤 C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: 3268e5b124be40313bdc97b4c95d935ddd4f9160
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208536"
---
# <a name="fatal-error-c1092"></a>嚴重錯誤 C1092

編輯後繼續不支援對資料類型的變更; 需要先進行建置

您已變更，或自從上次成功的組建後，新增的資料類型。

- 編輯後繼續不支援變更現有的資料類型，包括類別、 結構或列舉的定義。 您必須停止偵錯，並建置應用程式。

- 編輯後繼續不支援的新資料類型，如果程式資料庫檔案，例如 vc*x*0.pdb (其中*x*是視覺效果的主要版本C++中使用) 是唯讀的。 若要加入的資料類型，編譯器必須在寫入模式中開啟的.pdb 檔案。

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>若要移除這個錯誤，而不需要結束目前的偵錯工作階段

1. 請將資料類型改回錯誤之前的狀態。

1. 從 [偵錯]  功能表選擇 [套用程式碼變更] 。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>移除這個錯誤，而不變更您的原始程式碼

1. 從 [偵錯]  功能表選擇 [停止偵錯] 。

1. 從 [建置]  功能表選擇 [建置] 。

如需詳細資訊，請參閱 [支援的程式碼變更](/visualstudio/debugger/supported-code-changes-cpp)。