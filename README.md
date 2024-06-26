# nix_package-template
Learn Making Nix pkg
```nix
{stdenv, lib, fetchFromGithub, gcc, make, pkgconfig, binutils };
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

meta = with lib; {
 description = "Fully Nix Based Package to Run All IDX templates";
 homepage = "https://github.com/mg3994/${pname}";
 license = licenses.mit;
 platforms = platforms.unix;
};



}

```

# OR
# from url

```nix
{stdenv, lib, fetchurl, runTimePackage, fetchFromGithub, gcc, make, pkgconfig, binutils };
stdenv.mkDerivation rec {
 pname = "antinna";
 version = "1.0.0";

src = fetchurl {
url = "https://example.com/${pname}-${version}-${stdenv.hostPlatform.system}.tar.gz";
sha256 = "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA";
};
dontBuild = true;
installPhase = ''
mkdir -p $out/bin
cp ${pname} $out/bin/
'';

propagatedBuildInputs = [ runTimePackage ] # you have to replace it with required runTime packages like gzip and all # those
meta = with lib; {
 description = "Fully Nix Based Package to Run All IDX templates";
 homepage = "https://github.com/mg3994/${pname}"; # or use example.com
 license = licenses.mit;
 platforms = platforms.unix;
};

}


```

