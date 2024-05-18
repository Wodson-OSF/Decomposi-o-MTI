# Decomposi-o-MTI/**
 * Gera todas as subsequências de uma palavra composta apenas por letras maiúsculas ou minúsculas.
 *
 * @param word Palavra a ser analisada.
 * @return Uma string contendo todas as subsequências da palavra, separadas por vírgulas.
 *         Por exemplo, subsequences("abc") retorna "abc,ab,bc,ac,a,b,c,".
 */
public static String subsequences(String word) {
    // Caso base: se a palavra estiver vazia, a única subsequência é a string vazia.
    if (word.isEmpty()) {
        return "";
    } else {
        // Divide a palavra na primeira letra e no restante da palavra.
        char firstLetter = word.charAt(0);
        String restOfWord = word.substring(1);

        // Obtém todas as subsequências do restante da palavra.
        String subsequencesOfRest = subsequences(restOfWord);

        // Constrói a string de resultado com todas as subsequências.
        String result = "";
        for (String subsequence : subsequencesOfRest.split(",", -1)) {
            // Adiciona a subsequência atual com e sem a primeira letra.
            result += "," + subsequence;
            result += "," + firstLetter + subsequence;
        }

        // Remove a vírgula inicial extra.
        result = result.substring(1);

        // Retorna a string de resultado contendo todas as subsequências.
        return result;
    }
}
