# Beyond Anti Evil Maid

*In 2011, Joanna Rutkowska unveiled an easy-to-use tool for mitigating many attacks on system boot chains by using the TPM - the Anti Evil Maid. Unfortunately the implementation was difficult to incorporate into normal system boot in a secure manner - anybody able to observe a user could recreate the secret. This presentation describes a method to allow systems to prove their identity to the user without making it trivial for attackers to mimic a secure boot and extract secrets from the user, and why the state of modern hardware means this may still not be enough.*

Matthew Garrett

- Trusted Platform Module
  - Signing of code.
  - Each module calculates the checksum of the next module the next before execution.
  - Creates a chain of hashes H_n = H(H_(n-1), V), which is verified upon use.
  - TPM keys can be restricted to PCR state.
  - Data is not hashed.
  - Signing needs to be verified against a certificate chain, leading up to the hardware vendor.
- TPM features.
  - Can create and store crypto keys.
  - Only stored in TPM; not memory or on disk.
  - Storage is dependent on TPM state, 
  - Can be used to create disk crypto keys.
  - There's no authenication; the system will just boot.
    - Doesn't prevent booting from disk as there's no password prompt.
    - Introducing password promts is hard; no way of telling if the system is still trustworthy.
- Anti evil maid.
  - Encrypt a phrase known only to the user, store in TPM.
  - Show on screen at boot, which proves that the system hasn't been tampered with.
    - Unless the entire system has been compromised.
  - What about a time-dependent one-time password?
    - Same systems banks use for logins through tokens.
    - Have the system show a six-digit code.
    - Compare to an external system, like your cellphone.
    - If the numbers match on both systems, the system is correct.
    - Time-dependent secret will exist in RAM though.
      - Use IOMMU to be more secure?
    - TPM can sign with time of day; code can now be verified on the system level.
    - Can be done with an externally generated crypto key shared betwen the TPM and mobile phone.
      - External key can be extracted from TPM through a design flaw.
      - Might be overcomplicating things.
- TPM execution can be tied to specific GPIO pins.
  - Can be used to turning on a LED.
    - Susceptible to easy hardware hacks.
  - Can be used to read data from NFC.
    - Store private key on NFC; system won't boot without NFC unit.
- Attackes.
  - "Managment Engine" still has access to memory through DMA.
  - TPM can be attacked physically.
  - Can't trust hardware designed and fabricated by others.
  - Even with open source CPU designs, who controlls the fabrication process?
- Open source.
  - https://github.com/mjg59/shim
  - https://github.com/mjg59/grub
  - https://github.com/mjg59/tpmtotp
