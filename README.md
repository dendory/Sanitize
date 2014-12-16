Sanitize
========
This is a simple Perl module to sanitize user input. Here are some examples of its use:

    use Sanitize;
    sanitize("fd gfd*#(sd)", alpha => 1); # Returns: "fggfdsd"
    sanitize("The ip is 192.168.3.53:80", ip => 1); # Returns: "192.168.3.53"
    sanitize("The ip is 192.168.3.53:80", port => 1); # Returns: "80"
    sanitize("The ip is 192.168.3.53:80", ip => 1, port => 1); # Returns: "192.168.3.53:80"
    sanitize("Blah", password => 1); # Returns: "****"
    sanitize("sf d54_d <script>alert('test');", html => 1); # Returns: "sf d54_d &lt;script&gt;alert('test');"
    sanitize("Some email is: joe@test.com, email me now", email => 1); # Returns: "joe@test.com"
    sanitize(" some thing ", rtrim => 1); # Returns: " some thing"
    sanitize(" some thing ", ltrim => 1); # Returns: "some thing "
    sanitize(" some thing ", nospace => 1); # Returns: "something"
    sanitize("This is a %3Cscript%3Ealert('test');", noquote => 1, noencoding => 1); # Returns: "This is a &lt;script&gt;alert(test);"
    validate("invalid email@some!host", email => 1); # Returns: 0
    validate("10.0.0.1", ip => 1); # Returns: 1
    validate("invalid.ip.7.4", ip => 1); # Returns: 0

