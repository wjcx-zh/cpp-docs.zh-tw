---
title: 使用多個結果集從某個預存程序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6393901839e8450ebc45b11f1d4bd2250da2ca56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106306"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>從預存程序使用多重結果集
大多數的預存程序傳回多個結果集。 這類預存程序通常包含一個或多個 select 陳述式。 取用者必須考慮此選項可處理所有結果集。  
  
### <a name="to-handle-multiple-result-sets"></a>若要處理多個結果集  
  
1.  建立`CCommand`類別`CMultipleResults`作為範本引數，並使用您所選擇的存取子。 通常，這是一個動態或手動存取子。 如果您使用另一種存取子時，您可能無法決定每個資料列集的輸出資料行。  
  
2.  如往常般執行預存程序並繫結資料行 (請參閱[How Do I 擷取資料嗎？](../../data/oledb/fetching-data.md))。  
  
3.  使用的資料。  
  
4.  呼叫`GetNextResult`上`CCommand`類別。 如果另一個結果資料列集可供使用，`GetNextResult`傳回 S_OK，如果您使用手動存取子，應該重建您的資料行。 如果`GetNextResult`會傳回錯誤，有可用的任何進一步的結果集合。  
  
## <a name="see-also"></a>另請參閱  
 [使用預存程序](../../data/oledb/using-stored-procedures.md)