---
title: "使用 TCHAR。H 含有 _MBCS 程式碼的資料型別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tchar.h
- TCHAR
dev_langs: C++
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 8eb50d8e49b195ffb3322bb30a8f147c2f248273
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>使用含有 _MBCS 程式碼的 TCHAR.H 資料類型
當資訊清單常數**_MBCS**是定義，在指定的一般文字常式對應至下列幾種常式的其中一個：  
  
-   適當地處理多位元組位元組、字元與字串的 SBCS 常式。 在此情況下，字串引數都必須是型別**char\***。 例如，`_tprintf`對應至`printf`; 字串引數以`printf`類型**char\***。 如果您使用**_TCHAR**泛用文字資料類型，為您的字串類型，型式和實質參數類型`printf`相符，因為**_TCHAR** \*對應至**char\***.  
  
-   MBCS 特定常式。 在此情況下，字串引數都必須是型別`unsigned` **char\***。 例如，`_tcsrev`對應至`_mbsrev`，會預期，並傳回類型的字串`unsigned` **char\***。 如果您使用**_TCHAR**泛用文字資料類型為您的字串類型，會產生的類型衝突，因為**_TCHAR**對應至輸入`char`。  
  
 下面是防止此類型衝突 (以及可能會產生的 C 編譯器警告或 C++ 編譯器錯誤) 的三種解決方式：  
  
-   使用預設行為。 Tchar.h 常式在執行階段程式庫中，如下列範例所示，提供一般文字常式的原型。  
  
    ```  
    char * _tcsrev(char *);  
    ```  
  
     在預設情況下的原型`_tcsrev`對應至`_mbsrev`透過 Libc.lib 中的 thunk。 這會變更的類型`_mbsrev`傳入參數和外寄的傳回值**_TCHAR \***  (也就是`char`  **\*** ) 至`unsigned``char` **\***. 這個方法可確保當您使用比對的型別**_TCHAR**，但由於函式呼叫的額外負荷相對比較慢。  
  
-   透過在您的程式碼中併入下列前置處理器陳述式，以內嵌方式使用函式。  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     這個方法會以一般文字常式會直接對應到適當的 MBCS 常式 Tchar.h 中提供內嵌函式 thunk。 下列程式碼摘錄 Tchar.h 從提供的執行方式的範例。  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     若您可以使用內嵌，這是最佳解決方式，因為它可以保證類型相符，而且沒有任何額外成本。  
  
-   使用直接對應，透過加入您的程式碼中的下列前置處理器陳述式。  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     若您不想使用預設行為或無法使用內嵌，此方法提供快速替代方式。 它會導致一般文字常式對應巨集所直接到常式，如下列範例從 Tchar.h 中的 MBCS 版本。  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
     當您採用這個方法時，您必須小心確保使用適當的資料類型的字串引數和傳回值的字串。 您可以使用型別轉型來確保符合適當的型別，或者您可以使用**_TXCHAR**泛用文字資料類型。 **_TXCHAR**對應至輸入`char`SBCS 程式碼，但對應至輸入中`unsigned` `char` MBCS 程式碼中。 如需一般文字巨集的詳細資訊，請參閱[泛用文字對應](../c-runtime-library/generic-text-mappings.md)中*執行階段程式庫參考*。  
  
## <a name="see-also"></a>另請參閱  
 [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)