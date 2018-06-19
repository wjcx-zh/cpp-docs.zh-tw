---
title: '如何： 將 system:: string 轉換為 wchar_t* 或 char* |Microsoft 文件'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- System::String, converting to char or wchar_t
- PtrToStringChars method
- System::String
- wchart type, converting System::String
- char data type, converting System::String to
ms.assetid: 385da01b-5649-4543-8076-e3e251243ff0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: db4b1955042b83b26ac8abfa9fa5b9b434d35a43
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33139757"
---
# <a name="how-to-convert-systemstring-to-wchart-or-char"></a>如何：將 System::String 轉換為 wchar_t* 或 char*
您可以使用`PtrToStringChars`中要轉換的 Vcclr.h<xref:System.String>到原生`wchar_t *`或`char *`。  這一律傳回寬的 Unicode 字串指標，因為 CLR 字串在內部是 unicode 資料類型。 您可以再轉換寬如下列範例所示。  
  
## <a name="example"></a>範例  
  
```  
// convert_string_to_wchar.cpp  
// compile with: /clr  
#include < stdio.h >  
#include < stdlib.h >  
#include < vcclr.h >  
  
using namespace System;  
  
int main() {  
   String ^str = "Hello";  
  
   // Pin memory so GC can't move it while native function is called  
   pin_ptr<const wchar_t> wch = PtrToStringChars(str);  
   printf_s("%S\n", wch);  
  
   // Conversion to char* :  
   // Can just convert wchar_t* to char* using one of the   
   // conversion functions such as:   
   // WideCharToMultiByte()  
   // wcstombs_s()  
   // ... etc  
   size_t convertedChars = 0;  
   size_t  sizeInBytes = ((str->Length + 1) * 2);  
   errno_t err = 0;  
   char    *ch = (char *)malloc(sizeInBytes);  
  
   err = wcstombs_s(&convertedChars,   
                    ch, sizeInBytes,  
                    wch, sizeInBytes);  
   if (err != 0)  
      printf_s("wcstombs_s  failed!\n");  
  
    printf_s("%s\n", ch);  
}  
```  
  
```Output  
Hello  
Hello  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)