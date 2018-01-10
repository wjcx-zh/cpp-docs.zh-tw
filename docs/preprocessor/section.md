---
title: "區段 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- section_CPP
- vc-pragma.section
dev_langs: C++
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc6035caeb3b2fe466d18ea92300b3135a6189f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="section"></a>section
在 .obj 檔案中建立區段。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma section( "section-name" [, attributes] )  
```  
  
## <a name="remarks"></a>備註  
 意義*區段*和*區段*是本主題中的可互換的。  
  
 區段定義之後，其仍適用於編譯的其餘部分。 不過，您必須使用[__declspec （allocate)](../cpp/allocate.md)或執行任何動作將會放在區段。  
  
 *區段名稱*是必要的參數，將會是區段的名稱。 名稱不得與任何標準區段名稱相衝突。 請參閱[/section](../build/reference/section-specify-section-attributes.md)如需建立區段時，不應該使用的名稱。  
  
 `attributes` 是選擇性的參數，其中包含一個或多個逗號分隔的屬性，這些是您要指派給該區段的屬性。 可能的 `attributes` 為：  
  
 **read**  
 允許對於資料進行讀取作業。  
  
 **write**  
 允許對於資料進行寫入作業。  
  
 **執行**  
 允許執行程式碼。  
  
 **共用**  
 讓所有載入影像的處理序共用區段。  
  
 **nopage**  
 將區段標記為不可分頁；適用於 Win32 裝置驅動程式。  
  
 **無快取記憶體**  
 將區段標記為不可快取；適用於 Win32 裝置驅動程式。  
  
 **捨棄**  
 將區段標記為可捨棄；適用於 Win32 裝置驅動程式。  
  
 **remove**  
 標記為不常駐記憶體; 區段虛擬裝置驅動程式 (V*x*D) 只。  
  
 如果您未指定屬性，區段將會具有讀取和寫入屬性。  
  
## <a name="example"></a>範例  
 在下列範例中，第一個指令會識別區段及其屬性。 由於未以 `j` 宣告整數 `mysec`，因此不會將該整數置於 `__declspec(allocate)`；`j` 會包含在資料區段中。 整數 `i` 屬於 `mysec`，這是其 `__declspec(allocate)` 儲存類別屬性的結果。  
  
```  
// pragma_section.cpp  
#pragma section("mysec",read,write)  
int j = 0;  
  
__declspec(allocate("mysec"))  
int i = 0;  
  
int main(){}  
```  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)