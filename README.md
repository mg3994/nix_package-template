# nix_package-template
Learn Making Nix pkg
```nix
{stdenv, fetchFromGithub, gcc, make, pkgconfig, binutils };
stdenv.mkDerivation rec {
 pname = "antinna";
 version = "1.0.0";

src = fetchFromGithub {
 owner = "Manish";
 repo = pname;
 rev = "v${version}";
 sha256 = "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA";
};
 buildInputs = [ gcc make pkgconfig binutils ];

meta = with stdenv.lib; {
 description = "Fully Nix Based Package to Run All IDX templates";
 homepage = "https://github.com/mg3994/${pname}";
 license = licenses.mit;
 platforms = platforms.unix;
};



}

```
