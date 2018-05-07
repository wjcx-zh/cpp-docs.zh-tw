---
title: '如何： 存取 system:: string 中的字元 |Microsoft 文件'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ed9682492eedc915919758d42d5594560cb4a83a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-characters-in-a-systemstring"></a>如何：存取 System::String 中的字元
您可以存取的字元<xref:System.String>物件的未受管理的高效能呼叫函式採用`wchar_t*`字串。 這個方法會產生的第一個字元的內部指標<xref:System.String>物件。 此指標可以可直接操作或釘選並傳遞至函式必須要有一般`wchar_t`字串。  
  
## <a name="example"></a>範例  
 `PtrToStringChars` 傳回<xref:System.Char>，這是內部指標 (也稱為`byref`)。 因此，它是受記憶體回收限制。 您不需要釘選此指標，除非您打算將它傳遞至原生函式。  
  
 請考慮下列程式碼：  Pin 不需要因為`ppchar`內部指標，且如果記憶體回收行程會移動它所指向的字串，它也會更新`ppchar`。 不含[pin_ptr (C + + /CLI)](../windows/pin-ptr-cpp-cli.md)，程式碼將會運作，而且不具有可能造成的效能衝擊釘選。  
  
 如果您要傳入`ppchar`原生函式，則它必須是 pin 指標，記憶體回收行程將無法更新任何 unmanaged 的堆疊框架上的指標。  
  
```  
// PtrToStringChars.cpp  
// compile with: /clr  
#include<vcclr.h>  
using namespace System;  
  
int main() {  
   String ^ mystring = "abcdefg";  
  
   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );  
  
   for ( ; *ppchar != L'\0'; ++ppchar )  
      Console::Write(*ppchar);  
}  
```  
  
```Output  
abcdefg  
```  
  
## <a name="example"></a>範例  
 此範例所示釘選需要的位置。  
  
```  
// PtrToStringChars_2.cpp  
// compile with: /clr  
#include <string.h>  
#include <vcclr.h>  
// using namespace System;  
  
size_t getlen(System::String ^ s) {  
   // Since this is an outside string, we want to be secure.  
   // To be secure, we need a maximum size.  
   size_t maxsize = 256;  
   // make sure it doesn't move during the unmanaged call  
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);  
   return wcsnlen(pinchars, maxsize);  
};  
  
int main() {  
   System::Console::WriteLine(getlen("testing"));  
}  
```  
  
```Output  
7  
```  
  
## <a name="example"></a>範例  
 內部指標具有原生 c + + 指標的所有屬性。 例如，使用連結的資料結構並進行插入和刪除使用只有一個指標：  
  
```  
// PtrToStringChars_3.cpp  
// compile with: /clr /LD  
using namespace System;  
ref struct ListNode {  
   Int32 elem;   
   ListNode ^ Next;  
};  
  
void deleteNode( ListNode ^ list, Int32 e ) {   
   interior_ptr<ListNode ^> ptrToNext = &list;  
   while (*ptrToNext != nullptr) {  
      if ( (*ptrToNext) -> elem == e )  
         *ptrToNext = (*ptrToNext) -> Next;   // delete node  
      else  
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node  
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)