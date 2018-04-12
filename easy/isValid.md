bool isValid(char* s) {
    char nextChar(char s){
        switch(s){
            case ')': return '(';
            case ']': return '[';
            case '}': return '{';
            default: return 'other';    
        }
    }
    int length = strlen(s);
    if(length%2) return false;
    if(*(s+length-1)=='('|*(s+length-1)=='['|*(s+length-1)=='{') 
        return false;
    char* x = (char*)malloc((length/2)*sizeof(char));
    char* xx = (char*)malloc((length/2)*sizeof(char));
    char y=*x;
    char yy = *xx;
    int j=0;
    int jj=0;
    for(int i = 0; i< length; i++){
        if(*(s+i)=='(' | *(s+i)=='['|*(s+i)=='{'){
            x[j] = s[i];
            j++;
        }
        else{
            xx[jj] = *(s+i);
            jj++;
            j--;
            if(*(x+j)!=nextChar(*(s+i))) return false;
        }
    }
    if(yy==*xx|y==*x) 
        return false;
    else
        return true;
}
