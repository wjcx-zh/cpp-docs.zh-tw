---
title: 包含共用 （唯讀） 或計算符號 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.shared.calculated
dev_langs:
- C++
helpviewer_keywords:
- symbols, read-only
- symbols, shared
- symbols, calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 29449031485f1b701d6b6a1cfe671993c5ebc73a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589311"
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>包含共用 (唯讀) 或計算符號

當開發環境第一次讀取另一個應用程式所建立的資源檔時，會將所有包含的標頭檔標示為唯讀。 接著，您可以使用[資源包含對話方塊](../windows/resource-includes-dialog-box.md)新增額外的唯讀符號標頭檔。

您可能想要使用唯讀符號定義的其中一個原因是，您想要將它們在數個專案之間共用的符號檔中運用。

當您搭配使用現有資源與符號定義，且這些定義使用運算式而非是簡單的整數來定義符號值，您也可以使用包含的符號檔。 例如: 

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```

環境會正確解譯這些計算的符號，前題是：

- 計算的符號會放置在唯讀符號檔案。

- 您的資源檔包含已指派這些計算的符號的資源。

- 預期是數值運算式。

> [!NOTE]
> 如果預期字串或數值運算式，則不會評估運算式。

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>在資源檔中包含共用 (唯讀) 符號

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇[Resource Includes](../windows/resource-includes-dialog-box.md)從捷徑功能表。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 **唯讀符號指示詞**方塊中，使用`#include`編譯器指示詞來指定您想要保存唯讀符號的檔案。

   請勿呼叫檔案`Resource.h`，因為這是通常由主要的符號標頭檔的檔名。

   > [!NOTE]
   > **重要**完全依照您輸入您在唯讀符號指示詞中所輸入的內容包含在資源檔。 請確定您輸入的內容不包含任何拼字或語法錯誤。

   使用**唯讀符號指示詞**方塊以包含僅具有符號定義的檔案。 不包含資源定義；否則在儲存檔案時會建立重複的資源定義。

3. 將符號放在您指定的檔案。

   每次開啟資源檔時，都會評估以這種方式包含的檔案中符號，但在儲存檔案時，並不會在磁碟上取代它們。

4. 按一下 [確定 **Deploying Office Solutions**]。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[符號名稱限制](../windows/symbol-name-restrictions.md)  
[符號值限制](../windows/symbol-value-restrictions.md)  
[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)  
[符號：資源識別項](../windows/symbols-resource-identifiers.md)