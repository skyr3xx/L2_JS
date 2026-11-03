// z1
function hasTwoCubeSums(n) {
	//TODO
  let max = Math.ceil(Math.cbrt(n));
  let count = 0
  for(let i = 0; i < max; i += 1)
    {
      let x = Math.cbrt(n - i**3);
      if(x%1 == 0) count += 1
    }
  return count >= 4
}
// 

// z2
function ipv4Parser(ip, mask){
  //your code here
  let splitip = ip.split('.');
  let splitmask = mask.split('.');
  let nb = []; let hi = [];
  for(let i = 0; i < 4; i += 1)
    {
      nb[i] = Number(splitip[i]) & Number(splitmask[i]);
      hi[i] = Number(splitip[i]) & ~Number(splitmask[i]);
    }
  return [nb.join('.'), hi.join('.')];
}
// 

// z3
function whatCentury(year)
{
  // code must go here
  let cent = Math.ceil(Number(year) * 0.01);
  if(cent < 20) return cent + "th";
  switch(cent%10)
    {
        case 1: return cent + "st"; break;
        case 2: return cent + "nd"; break;
        case 3: return cent + "rd"; break;
        default: return cent + "th"; break;
    }
}
// 

// z4
function findMissing(list) {  
  let l = list.length;
  let md = list[1] - list[0];
  for(let i = 1; i < l-1; i+=1)
    {
      if(list[i+1] - list[i] < md) md = list[i+1] - list[i];
    }
  for(let i = 0; i < l-1; i+=1)
    {
      if(list[i] + md != list[i+1]) return list[i] + md;
    }
}
// 

// z5
function primeFactors(n){
    //your code here
  let count = 0;
  let dig = []; let id = [];
for(let i = 2; n != 1; i+=1)
    {
      if (n%i != 0) continue
      while(n%i === 0)
        {
          n = n / i
          count++
        }
          dig.push(i);
          id.push(count);
          count = 0;
    }
  let result = "";
  for(let i = 0; i < dig.length; i +=1)
    {
      if(id[i] > 1) result += `(${dig[i]}**${id[i]})`;
      else result += `(${dig[i]})`;
    }
  return result;
}
// 

// z6
function toWeirdCase(string){
  //TODO
  let arr = string.split("");
  let count = 0;
  for(let i = 0; i < arr.length; i+=1)
    {
      if(arr[i] === ' ')
        {
          count = 0; continue;
        }
      if(count%2 === 0)
        {
          arr[i] = arr[i].toUpperCase();
          count++;
          continue;
        }
      else arr[i] = arr[i].toLowerCase();
      count++;
      continue;
    }
  return arr.join("");
}
// 

// z7
function wave(str){
  // Code here
  let result = [];
  for(let i = 0; i < str.length; i+=1)
    {
      let arr = str.split("");
      for(let j = 0; j < arr.length; j+=1) arr[j]=arr[j].toLowerCase();
      if(arr[i] === " ") continue;
      arr[i] = arr[i].toUpperCase();
      result.push(arr.join(""));
    }
  return result;
}
//

// z8
function expandedForm(num) {
  // Your code here
  let digs = []
  let str = num.toString();
  let arr = str.split("");
  for(let i = 0; i < arr.length; i+=1)
    {
      if(arr[i] === '0') continue;
      digs.push(`${arr[i]}` + '0'.repeat(arr.length-1-i));
    }
  digs = digs.join(' + ')
  return digs;
}
//

// z9
function solution(str){
  let arr = str.split("");
  let result = [];
  if(str.length%2 != 0) arr.push('_');
  for(let i = 0; i < arr.length; i+=2)
    {
      result.push(arr[i] + arr[i+1]);
    }
  return result;
}
//

// z10
function bingo(ticket, win){
  let count = 0;
  for(let i = 0; i < ticket.length; i+=1)
    {
      if(ticket[i][0].indexOf(String.fromCharCode(ticket[i][1])) != -1)
        {
          count++
        }
    }
  if(count >= win) return 'Winner!'
  else return 'Loser!'
}
//

// z11
function domainName(url){
  //your code here
  let nurl = url;
  if(nurl.startsWith('http://')) nurl = nurl.slice(7);
  else if(nurl.startsWith('https://')) nurl = nurl.slice(8);
  if(nurl.startsWith('www.')) nurl = nurl.slice(4);
  return nurl.split('.')[0];
}
//

// z12
function longest(arr, n) {
//code me
  let m = arr.length; let s;
  for(let i = 0; i < m; i+=1)
    {
      s = false;
      for(let j = 0; j < m-i-1; j+=1)
        {
          if(arr[j].length < arr[j+1].length)
            {
              let t = arr[j];
              arr[j] = arr[j+1];
              arr[j+1] = t
              s = true
            }
        }
      if(!s) break;
    }
    return arr[n-1];
}
//

// z13
function hexStringToRGB(hexString) {
  return {r:parseInt(hexString.slice(1, 3), 16), g:parseInt(hexString.slice(3, 5), 16), b:parseInt(hexString.slice(5, 7), 16)};
}
// 

// z14
function isCircleSorted( arr ){
  // ...
  let count = 0;
  for(let i = 0; i < arr.length; i+=1)
    {
      if(arr[i] > arr[(i+1) % arr.length]) count++
    }
  return count < 2
}
// 

// z15
function howManyTimes(time1,time2){
  //coding here...
  let datetime1 = new Date(time1);
  let datetime2 = new Date(time2);
  let count = 0;
  while(datetime1 < datetime2)
  {
    let h = datetime1.getHours();
    let m = datetime1.getMinutes();
    let s = datetime1.getSeconds();
    let h12 = h%12 === 0 ? 12 : h%12;
    if(m === 30 && s === 0)  count+=1
    else if(m === 0 && s < h12) count+=1
    datetime1.setSeconds(datetime1.getSeconds() + 1);
  }
  return count;
}
//

// z16
