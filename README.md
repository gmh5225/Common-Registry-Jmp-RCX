# Common-Registry-Jmp-RCX
https://www.unknowncheats.me/forum/anti-cheat-bypass/501925-undetected-kernel-communication-method.html

```C++
NTSTATUS __stdcall DriverEntry(PDRIVER_OBJECT DriverObject, PUNICODE_STRING RegistryPath)
{
  char *nvraid_base; // rax
  char *jmp_rcx_in_nvraid; // rbx

  nvraid_base = (char *)get_sys_module_1400010E8(L"nvraid.sys");
  if ( !nvraid_base )
    return 0xC0000008;
  jmp_rcx_in_nvraid = find_jmp_rcx_140001070(nvraid_base);
  if ( !jmp_rcx_in_nvraid )
    return 0xC0000225;
  RtlInitUnicodeString(&String2, L"GlobalDeviceUpdateTime");// reg key
  return CmRegisterCallback((PEX_CALLBACK_FUNCTION)jmp_rcx_in_nvraid, sub_1400011E0, stru_140003000);
}
```
