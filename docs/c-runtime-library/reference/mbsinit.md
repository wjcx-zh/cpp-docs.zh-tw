---
title: "mbsinit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "mbsinit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbsinit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "mbsinit 函式"
ms.assetid: 4618555b-baaa-4d04-93fa-36abae411034
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbsinit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

追蹤多位元組字元轉換的狀態。  
  
## 語法  
  
```  
  
      int mbsinit(  
   const mbstate_t* ps  
);  
```  
  
#### 參數  
 `ps`  
 對 [mbstate\_t](../../c-runtime-library/standard-types.md) 變數的指標。  
  
## 傳回值  
 如果 `ps` 是空的或是不在轉換之中，則不是零。  
  
## 備註  
 當使用採用 **mbstate\_t** 指標的 ANSI 函式，將 `mbstate_t` 的位址會傳回有關在緩衝區的最後一個位元組的轉換。  
  
 需要安裝適當的字碼頁以支援您的多位元組字元。  
  
## 範例  
  
```  
// crt_mbsinit.cpp  
#include <stdio.h>  
#include <mbctype.h>  
#include <string.h>  
#include <locale.h>  
#include <cwchar>  
#include <xlocinfo.h>  
  
#define   BUF_SIZE   0x40  
  
wchar_t      g_wcBuf[BUF_SIZE] = L"This a wc buffer that will be over written...";  
char      g_mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";  
int      g_nInit = strlen(g_mbBuf);  
  
int MbsinitSample(char* szIn, wchar_t* wcOut, int nMax)  
{  
   mbstate_t   state = {0};  
   size_t      nConvResult, nmbLen = 0, nwcLen = 0;  
   wchar_t*   wcCur = wcOut;  
   wchar_t*   wcEnd = wcCur + nMax;  
   const char*   mbCur = szIn;  
   const char*   mbEnd = mbCur + strlen(mbCur) + 1;  
   char*      szLocal = setlocale(LC_ALL, "japanese");  
  
   printf("Locale set to: \"%s\"\n", szLocal);  
  
   if   (_setmbcp(_MB_CP_LOCALE) != -1)  
   {  
      while   ((mbCur < mbEnd) && (wcCur < wcEnd))  
      {  
         nConvResult = mbrtowc(wcCur, mbCur, 1, &state);   
  
         switch   (nConvResult)  
         {  
            case 0:  
            {   // done  
               printf("Conversion succeeded!\nMB String: ");  
               printf(szIn);  
               printf("\nWC String: ");  
               wprintf(wcOut);  
               printf("\n");  
               mbCur = mbEnd;  
               break;  
            }  
  
            case -1:  
            {   // encoding error  
               printf("ERROR: The call to mbrtowc has detected an encoding error.\n");  
               mbCur = mbEnd;  
               break;  
            }  
  
            case -2:  
            {   // incomplete character  
               if   (!mbsinit(&state))  
               {  
                  printf("Currently in middle of mb conversion, state = %x\n", state);  
                  // state will contain data regarding lead byte of mb character  
               }  
  
               ++nmbLen;  
               ++mbCur;  
               break;  
            }  
  
            default:  
            {  
               if   (nConvResult > 2)   // Microsoft mb should never be larger than 2  
                  printf("ERROR: nConvResult = %d\n", nConvResult);  
  
               ++nmbLen;  
               ++nwcLen;  
               ++wcCur;  
               ++mbCur;  
               break;  
            }  
         }  
      }  
   }  
   else  
      printf("ERROR: _setmbcp(932) failed!");  
  
   return 0;  
}  
  
int main(int argc, char* argv[])  
{  
   return MbsinitSample(g_mbBuf, g_wcBuf, BUF_SIZE);  
}  
```  
  
## 範例輸出  
  
```  
Locale set to: "Japanese_Japan.932"  
Currently in middle of mb conversion, state = 9a  
Currently in middle of mb conversion, state = e0  
Currently in middle of mb conversion, state = f0  
Conversion succeeded!  
MB String: AaBbCcxXyYzZ  
WC String: AaBbCcxXyYzZ  
```  
  
## 請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)