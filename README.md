    program sortirovka;
    const c=10000;
    var 
    M1: array [1..c] of integer;
    N,i,j: integer;

    procedure BS(L, R: integer);
    var i,j,x,y : integer;
    begin
      i:=l; j:=r;
      x:=M1[(l+r) div 2];
      repeat
        while (M1[i] < x) do inc(i);
        while (x < M1[j]) do dec(j);
        if (i <= j) then
        begin
          y:=M1[i]; M1[i]:=M1[j]; M1[j]:=y;
          inc(i); dec(j);
        end;
      until (i > j);
      if (l < j) then BS(l,j);
      if (i < r) then BS(i,r);
    end;

    begin 
    readln(N);
    if (c >= N) and (N > 2) then 
      begin
      for i:=1 to N do readln (M1[i]);
      BS(1, N);
      writeln(N);
        for i:=1 to N do
        if (M1[i] mod 3 = 0) then write(M1[i]);
        for i:=1 to N do
        if (M1[i] mod 3 <> 0) then write(M1[i]);
      end
    else writeln ('error');
    end.         
