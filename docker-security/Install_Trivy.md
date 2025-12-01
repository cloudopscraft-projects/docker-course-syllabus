# update package lists
sudo apt-get update -y

# install helper packages needed for adding HTTPS apt repos and managing GPG keys
sudo apt-get install wget apt-transport-https gnupg lsb-release -y

# fetch Trivy repository GPG public key and convert it to a keyring file
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo gpg --dearmor -o /usr/share/keyrings/trivy.gpg

# add the Trivy repository to apt sources, referencing the signed keyring,
# and using the current distro codename (lsb_release -sc)
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" \
  | sudo tee /etc/apt/sources.list.d/trivy.list

# update package lists again so apt knows about packages in the new repo
sudo apt-get update -y

# install Trivy from the newly added repository
sudo apt-get install trivy -y
