# Authentication and Authorization

**Authorization + Resource Server Design**

```java
public String createAccessToken(Authentication authentication) {
    UserDetailsImpl userPrincipal = (UserDetailsImpl) authentication.getPrincipal();

    return Jwts.builder()
        .setSubject(userPrincipal.getEmail())
        .setIssuer("DAT152-Lecturer@TDOY")
        .claim("firstname", userPrincipal.getFirstname())
        .claim("lastname", userPrincipal.getLastname())
        .claim("roles", userPrincipal.getAuthorities().stream()
        .map(role -> role.getAuthority())
        .collect(Collectors.toList()))
        .setIssuedAt(new Date())
        .setExpiration(new Date(System.currentTimeMillis() + EXPIRE_DURATION))
        .signWith(key(), SignatureAlgorithm.HS256)
        .compact();
}

public boolean validateAccessToken(String token) {
    try {
        Jwts.parserBuilder().setSigningKey(SECRET_KEY).build().parse(token);
    return true;
    } catch(MalformedJwtException e) {
        Logger.error("JWT is invalid!", ex.getMessage());
    } catch(ExpiredJwtException ex) {
        LOGGER.error("JWT token is expired!", ex.getMessage());
    }
}
```

**3rd Party Authroization Server**

- Keycloak idP
-
